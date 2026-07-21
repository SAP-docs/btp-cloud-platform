<!-- loio2ac8621a868d473da005994a9e3bc7e4 -->

# Increase Verbosity of the Istio Ingress Logs

To diagnose connection issues, you may need more verbose logs in the Istio Ingress container. Such logs may help determine whether the request reaches the Ingress and what happens to it.



<a name="loio2ac8621a868d473da005994a9e3bc7e4__section_access_logs"/>

## Enable Access Logs

An access log is the main observability feature. It contains a detailed log entry for every request that is processed.

With Istio, you can enable access logging by the `Telemetry` custom resource \(CR\). To enable access logging for the Istio Ingress Gateway, run:

```
cat <<EOF | kubectl apply -f -
apiVersion: telemetry.istio.io/v1
kind: Telemetry
metadata:
  name: ingress-access-logs-enabler
  namespace: istio-system
spec:
  selector:
    matchLabels:
      istio: ingressgateway
  accessLogging:
    - providers:
      - name: envoy
EOF
```

As a result, the Ingress log contains access logs.

Example: When you run the following command:

```
curl -k --tls-max 1.0 https://httpbin.local.kyma.dev/headers
```

The Ingress log contains the following entry:

```
{"authority":"httpbin.local.kyma.dev","bytes_received":0,"bytes_sent":442,"connection_termination_details":null,"downstream_local_address":"10.42.0.9:8443","downstream_remote_address":"10.42.0.1:22564","duration":15,"method":"GET","path":"/headers","protocol":"HTTP/2","request_id":"b947e4b6-2965-4cca-af90-51e3a1f4673f","requested_server_name":"httpbin.local.kyma.dev","response_code":200,"response_code_details":"via_upstream","response_flags":"-","route_name":null,"start_time":"2026-06-30T09:09:58.374Z","upstream_cluster":"outbound|8000||httpbin.test.svc.cluster.local","upstream_host":"10.42.0.13:80","upstream_local_address":"10.42.0.9:35226","upstream_service_time":"13","upstream_transport_failure_reason":null,"user_agent":"curl/8.7.1","x_forwarded_for":"10.42.0.1"}
```



<a name="loio2ac8621a868d473da005994a9e3bc7e4__section_trace_logs"/>

## Enable Trace Logs

If the access log is insufficient, increase the log level of the Istio Ingress. You can do it at runtime, so it doesn't require redeployment.

```
for ingress_pod in $(kubectl get pod -n istio-system --no-headers --output=name -l app=istio-ingressgateway); do
    istioctl proxy-config log -n istio-system "${ingress_pod}" --level trace
done
```

The effect is immediate, and the Ingress log provides detailed information for every connection. It is very useful for diagnosing problems in lower layers, such as \(m\)TLS.

Example: The following request fails because the TLS version is too old:

```
curl -k --tls-max 1.0 https://httpbin.local.kyma.dev/headers
```

Such a request is not visible in the access log because the connection has not been established, and the HTTP protocol has not been involved yet. The Ingress log shows the ***UNSUPPORTED\_PROTOCOL*** error.

```
2026-07-01T06:17:13.289504Z	trace	envoy filter external/envoy/source/extensions/filters/listener/tls_inspector/tls_inspector.cc:107	tls inspector: new connection accepted	thread=20
2026-07-01T06:17:13.289609Z	trace	envoy misc external/envoy/source/common/network/tcp_listener_impl.cc:123	TcpListener accepted 1 new connections.	thread=20
2026-07-01T06:17:13.289623Z	trace	envoy filter external/envoy/source/common/network/listener_filter_buffer_impl.cc:95	onFileEvent: 1	thread=20
2026-07-01T06:17:13.289637Z	trace	envoy filter external/envoy/source/common/network/listener_filter_buffer_impl.cc:60	recv returned: 165	thread=20
2026-07-01T06:17:13.289643Z	trace	envoy filter external/envoy/source/extensions/filters/listener/tls_inspector/tls_inspector.cc:147	tls inspector: recv: 165	thread=20
2026-07-01T06:17:13.289676Z	trace	envoy filter external/envoy/source/extensions/filters/listener/tls_inspector/tls_inspector.cc:129	tls:onALPN(), ALPN: h2,http/1.1	thread=20
2026-07-01T06:17:13.289688Z	debug	envoy filter external/envoy/source/extensions/filters/listener/tls_inspector/tls_inspector.cc:138	tls:onServerName(), requestedServerName: httpbin.local.kyma.dev	thread=20
2026-07-01T06:17:13.289797Z	trace	envoy misc external/envoy/source/common/event/scaled_range_timer_manager_impl.cc:60	enableTimer called on 0x32633f9a7180 for 15000ms, min is 15000ms	thread=20
2026-07-01T06:17:13.289848Z	trace	envoy misc external/envoy/source/common/event/scaled_range_timer_manager_impl.cc:60	enableTimer called on 0x32633f9a7080 for 3600000ms, min is 3600000ms	thread=20
2026-07-01T06:17:13.289880Z	debug	envoy conn_handler external/envoy/source/common/listener_manager/active_tcp_listener.cc:162	[Tags: "ConnectionId":"388"] new connection from 10.42.0.1:6943	thread=20
2026-07-01T06:17:13.289886Z	trace	envoy main external/envoy/source/common/event/dispatcher_impl.cc:249	item added to deferred deletion list (size=1)	thread=20
2026-07-01T06:17:13.289889Z	trace	envoy main external/envoy/source/common/event/dispatcher_impl.cc:123	clearing deferred deletion list (size=1)	thread=20
2026-07-01T06:17:13.289897Z	trace	envoy connection external/envoy/source/common/network/connection_impl.cc:662	[Tags: "ConnectionId":"388"] socket event: 3	thread=20
2026-07-01T06:17:13.289905Z	trace	envoy connection external/envoy/source/common/network/connection_impl.cc:808	[Tags: "ConnectionId":"388"] write ready	thread=20
2026-07-01T06:17:13.289918Z	trace	envoy config external/envoy/source/common/tls/server_context_impl.cc:511	TLS context selection result: 0, before selectTlsContext	thread=20
2026-07-01T06:17:13.289928Z	trace	envoy config external/envoy/source/common/tls/server_context_impl.cc:519	TLS context selection result: 1, after selectTlsContext, selection result status: 0	thread=20
2026-07-01T06:17:13.290005Z	trace	envoy connection external/envoy/source/common/tls/ssl_handshaker.cc:152	[Tags: "ConnectionId":"388"] ssl error occurred while read: SSL	thread=20
2026-07-01T06:17:13.290020Z	debug	envoy connection external/envoy/source/common/tls/ssl_socket.cc:269	[Tags: "ConnectionId":"388"] remote address:10.42.0.1:6943,TLS_error:|268435696:SSL routines:OPENSSL_internal:UNSUPPORTED_PROTOCOL:TLS_error_end	thread=20
2026-07-01T06:17:13.290025Z	debug	envoy connection external/envoy/source/common/network/connection_impl.cc:313	[Tags: "ConnectionId":"388"] closing socket: 0	thread=20
2026-07-01T06:17:13.290068Z	trace	envoy connection external/envoy/source/common/network/connection_impl.cc:517	[Tags: "ConnectionId":"388"] raising connection event 0	thread=20
```

> ### Caution:  
> Such verbose logs may influence the Ingress performance, so switch it back to a lower level after diagnosis is completed. By default, the Ingress uses a *warn* level.

