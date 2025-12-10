<!-- loiocaaf1dc34c494ebd9ab005d362e9f016 -->

# Python Buildpack: Troubleshooting

This page provides solutions on known issues related to the Python buildpack.

If you can't find a solution to your problem, create an incident to component **`BC-CP-CF-BLDP`**.

To learn how to start, see: [Troubleshooting](troubleshooting-073b7fc.md)



<a name="loiocaaf1dc34c494ebd9ab005d362e9f016__section_np5_python_aaa"/>

## Error: Could not install python: no match for 3.x.x



### Problem

You are trying to deploy or restage a working Python application but it suddenly fails.



### Reason

If an existing application was working fine, and after being redeployed or restaged it fails for no logical reason, take a look at the logs. It might be that the Python version you're using has been recently removed from the latest releases in the [community buildpack](https://github.com/cloudfoundry/python-buildpack/releases).

For example: You are using Python v **3.10.1**, and in the logs you see:

```
Could not install python: no match found for 3.10.1 in [3.8.19 3.9.19 3.10.14 3.11.9 3.12.5] 
```



### Solution

To make your application work again, go to the **`runtime.txt`** file and update the Python version like this:

```
python-3.10.x
```

You can also upgrade to a higher major version \(11, 12 or 13\). In this case, set the runtime analogically:

-   ```
python-3.11.x
```

-   ```
python-3.12.x
```

-   ```
python-3.13.x
```


