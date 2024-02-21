<!-- loioc1059e056aad406297addcd177a4fb7c -->

# Memory Calculator V1 \(SAP JVM Memory Calculator\)

> ### Remember:  
> This memory calculator is optional, and you can activate it by adding the following environment variable:
> 
> ```
> ---
> applications:
> - name: <app-name>
>   ...
>   env:
>     MEMORY_CALCULATOR_V1: true
>   ...
> ```



<a name="loioc1059e056aad406297addcd177a4fb7c__section_sgj_4ky_13b"/>

## General Information

When pushing applications to Cloud Foundry, application developers could specify the memory limit of the application.

The main goal of the SAP JVM Memory Calculator is to provide mechanism to fine tune the Java Virtual Machine \(JVM\) in terms of restricting the JVM's memory to grow below this memory limit.

There are three memory types, which can be sized - **heap**, **metaspace** and **stack**. For each memory type there is a command-line option, which must be passed to the JVM:

-   The initial and maximum size of the *heap* memory is controlled by the `-Xms` and `-Xmx` options, respectively.

-   The initial and maximum size of the *metaspace* memory is controlled by the `-XX:MetaspaceSize` and `-XX:MaxMetaspaceSize` options, respectively.

-   The size of the *stack* is controlled by the `-Xss` option.




<a name="loioc1059e056aad406297addcd177a4fb7c__section_w11_n5w_42b"/>

## Default Settings

The SAP Java Buildpack is delivered with a default built-in configuration of the memory sizing options in YML format - `config/sapjvm.yml` \(path related to the buildpack archive\). That configuration file is parsed during application staging, and the memory configuration specified in it is used for calculating the memory sizes of the *heap*, *metaspace* and *stack*.

The default structure of the `config/sapjvm.yml` configuration file is the following:

> ### Sample Code:  
> config/sapjvm.yml
> 
> ```
> ---
> repository_root: "{default.repository.root}/sapjvm/{platform}/{architecture}"
> version: +
> default_keystore_pass: changeit 
> memory_calculator:
>   version: 1.+
> repository_root: "{default.repository.root}/memory-calculator/{platform}/{architecture}"
> memory_sizes:
>   heap:
>   metaspace: 64m..
>   stack:
>   native:
> memory_heuristics:
>   heap: 75
>   metaspace: 10
>   stack: 5
>   native: 10
> memory_initials:
>   heap: 100%
>   metaspace: 100%
> memory_settings:
>   codecache:
>   directmemory:
> memory_calculator_v2:
>   version: 1.+
>   repository_root: "{default.repository.root}/memory-calculator-v2/{platform}/{architecture}"
>   class_count: 
>   stack_threads: 250
> ```

The **memory\_calculator** section encloses the input data for the memory calculation techniques utilized in determining the JVM memory sizing options.

-   *heap* – configure sizing options for the Java heap. Affects JVM options `-Xms` and `-Xmx`

-   *metaspace* – configure sizing options for the metaspace. Affects JVM options `-XX:MetaspaceSize` and `-XX:MaxMetaspaceSize`

-   *stack* – configure sizing options for the stack. Affects JVM option `-Xss`

-   *native* – serves to represent the rest of the memory \(different from *heap*, *stack*, *metaspace*\) in the calculations performed by the SAP JVM Memory Calculator. No JVM options are affected by this setting.

-   *memory\_heuristics* – this section defines the proportions between the memory regions addressed by the memory calculator. The ratios above will result in a *heap* space that is about 7.5 times larger than the *metaspace* and *native*; *stack* will be about half of the *metaspace* size.

-   *memory\_sizes* – this section defines sizes of the corresponding memory regions. The size of the memory region could be specified in kilobytes \(by using the K symbol\), megabytes \(by using the M symbol\) and gigabytes \(by using the G symbol\).


    <table>
    <tr>
    <th valign="top">

    Syntax
    
    </th>
    <th valign="top">

    Range
    
    </th>
    <th valign="top">

    Value that satisfies the Range
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    120M
    
    </td>
    <td valign="top">
    
    120M
    
    </td>
    <td valign="top">
    
    120M
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    120M..
    
    </td>
    <td valign="top">
    
    \[120M\)
    
    </td>
    <td valign="top">
    
    \>=120M
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    120M..150M
    
    </td>
    <td valign="top">
    
    \[120M, 150M\]
    
    </td>
    <td valign="top">
    
    \>=120M & <=150M
    
    </td>
    </tr>
    </table>
    
-   *memory\_initials* - this section defines initial and maximum values for *heap* and *metaspace*. By default, the initial values for *heap* and *metaspace* are set to 100%. That means, the memory calculation will result in **\-Xms=-Xmx** and **\-XX:MetaspaceSize=-XX:MaxMetaspaceSize**. If those values are set to 50%, then **\-Xmx = 2\*-Xms** and **\-XX:MaxMetaspaceSize=2\*-XX:MetaspaceSize**.

-   *memory\_settings* - for details, see [Java Out Of Memory Behavior](java-out-of-memory-behavior-588cfd9.md)

-   *memory\_calculator\_v2* - for details, see [Memory Calculator V2](memory-calculator-v2-8eef959.md)




<a name="loioc1059e056aad406297addcd177a4fb7c__section_x32_fww_42b"/>

## Customizing the Default Settings

There are two ways to customize the default settings - during application staging and during application runtime.



### Customizing the defaults during application staging

-   Customize the memory options by using the *JBP\_CONFIG\_SAPJVM* environment variable

    ```
      ---
      applications:
      - name: <app-name>
        memory: 512M
      ...
        env:
          JBP_CONFIG_SAPJVM:  "[memory_calculator: {memory_heuristics: {heap: 85, stack: 10}}]"
    ```

-   Customize the memory options by using the *JBP\_CONFIG\_SAPJVM\_MEMORY\_\** environment variables

    ```
      ---
      applications:
      - name: <app-name>
        memory: 512M
      ...
        env:
          JBP_CONFIG_SAPJVM_MEMORY_SIZES: 'heap:30m..400m,stack:2m..,metaspace:10m..12m'
          JBP_CONFIG_SAPJVM_MEMORY_WEIGHTS: 'heap:5,stack:1,metaspace:3,native:1'
          JBP_CONFIG_SAPJVM_MEMORY_INITIALS: "heap:50%,metaspace:50%"
    ```




### Customizing the defaults during application runtime

There are several ways to customize the SAP JVM Memory Calculator's settings during the application runtime. All of them include executing the `set-env` command – either on XSA or on Cloud Foundry. Below are some examples:

-   By using the JBP\_CONFIG\_SAPJVM environment variable

    ```
    cf set-env sapjbp-memcalc-sample JBP_CONFIG_SAPJVM "[memory_calculator: {memory_heuristics: {heap: 85, stack: 10}}]"
    ```

-   Customize the memory sizes by using the JBP\_CONFIG\_SAPJVM\_MEMORY\_SIZES environment variable

    ```
    cf set-env myapp JBP_CONFIG_SAPJVM_MEMORY_SIZES 'heap:30m..400m,stack:2m..,metaspace:10m..12m'
    ```

-   Customize the memory weights by using the JBP\_CONFIG\_SAPJVM\_MEMORY\_WEIGHTS environment variable

    ```
    cf set-env myapp JBP_CONFIG_SAPJVM_MEMORY_WEIGHTS 'heap:5,stack:1,metaspace:3,native:1'
    ```

-   Customize the memory initials by using the JBP\_CONFIG\_SAPJVM\_MEMORY\_INITIALS environment variable

    ```
    cf set-env myapp JBP_CONFIG_SAPJVM_MEMORY_INITIALS "heap:50%,metaspace:50%"
    ```




<a name="loioc1059e056aad406297addcd177a4fb7c__section_zwr_gzw_42b"/>

## Algorithm

When given certain memory limit, the memory calculator will try to calculate memory sizes for *heap*, *metaspace*, *stack* and *native* in a way that satisfies the proportions configured with the *memory\_heuristics*. Then the calculator will validate and adjust those sizes against the configured *memory\_sizes*.

Let's say that the calculated value for *heap*, according to the *memory\_heuristics*, is 120M. Let's assume that the *memory\_sizes* configuration for heap is 10M..100M. Even though 120M goes beyond the configured range, according to *memory\_heuristics*, 120M could be allocated for heap and the chosen value for *heap* size would be 100M. The calculation goes on until sizes \(*heap*, *metaspace*, *stack*, and *native*\) are calculated for all of the regions. Finally, the *memory\_initials* will be respected. This would affect the values of `-Xms`, `-Xms`, `-XX:MetaspaceSize`, and `-XX:MaxMetaspaceSize`.



### Example 1 \(memory limit of 1G with default settings of the memory calculator\)


<table>
<tr>
<th valign="top">

Memory limit

</th>
<th valign="top">

Memory calculator settings

</th>
</tr>
<tr>
<td valign="top">

1G

</td>
<td valign="top">

default

</td>
</tr>
</table>

First, the algorithm will try to estimate the number of threads for the given *memory\_limit* and *memory\_heuristics* given 1M per thread. This way, we'll have `estimated_number_of_threads`=*\(\(5/100\)\*1024M\)* = *51.2M* space for *stack*. Considering 1M per thread \(which by default is the `-Xss` size of the SAP JVM\), we'll get `estimated_number_of_threads`=*51.2*

1.  Apply the configured `memory_heuristics`:

    -   *heap*: \(75/100\)\* 1024M = 768M

    -   *metaspace*: \(10/100\) \* 1024M = 104857K

    -   *stack*: \(5/100\) \* 1024M = 51.2M

    -   *native*: \(10/100\) \* 1024M = 104858K


2.  Apply the configured `memory_sizes`:

    There is a memory range defined for *metaspace*, which is 64.

    The value 104857K calculated in step1 for *metaspace* satisfies the range.

3.  Apply the `memory_initials`:

    -   *\-Xms*: 100% \* 768M = 768M

    -   *\-Xmx*: 768M

    -   *\-XX:MetaspaceSize*: 100% \* 104857K = 104857K

    -   *\-XX:MaxMetaspaceSize*: 104857K

    -   *\-Xss: stack* / estimated\_number\_of\_threads = 51.2M / 51.2 = 1M





### Example 2 \(memory limit of 1G with customized settings of the memory calculator\)


<table>
<tr>
<th valign="top">

Memory limit

</th>
<th valign="top">

Memory calculator settings

</th>
</tr>
<tr>
<td valign="top">

1G

</td>
<td valign="top">

`memory_sizes`:

-   *metaspace*: 64m..70m


`memory_heuristics`:

-   *heap*: 75

-   *metaspace*: 10,

-   *stack*: 5

-   *native*: 10


`memory_initials`:

-   *heap*: 100%

    *metaspace*: 50%




</td>
</tr>
</table>

First, the algorithm will try to estimate the number of threads for the given *memory\_limit* and *memory\_heuristics* given 1M per thread. This way, we'll have `estimated_number_of_threads`=*\(\(5/100\)\*1024M\)* = *51.2M* space for *stack*. Considering 1M per thread \(which by default is the `-Xss` size of the SAP JVM\), we'll get `estimated_number_of_threads`=*51.2*.

**Round 1:**

1.  Apply the configured `memory_heuristics`:

    -   *heap* = \(75/100\) \* 1024M = 768M

    -   *metaspace* = \(10/100\) \* 1024M = 104857K

    -   *stack* = \(5/100\) \* 1024M = 51.2M

    -   *native*: \(10/100\) \* 1024M = 104857K


2.  Apply the configured `memory_sizes`:

    The *metaspace* should be between 60m and 70m. Since the value calculated in step 1 goes beyond this range, the chosen value for *metaspace* becomes 70M. This leads to a second round of calculation since there are \(104857K - 70M\) = 33177K, which are available to be distributed among the other regions - heap, stack, native.


**Round 2:**

The *metaspace* is already calculated, so its size is substracted from the memory limit leading to memory available for distribution, which is \(1G - 70M\) = 954M.

The same calculation takes place, this time the *metaspace* is not considered because it's already calculated.

1.  Apply the `memory_heuristics`:

    -   *heap* = \(75/90\) \* 954M = 795M

    -   *stack* = \(5/90\) \* 954M = 53

    -   *native* = \(10/90\) \* 954M = 106M


2.  Apply the `memory_sizes`:

    No settings for *heap*, *stack* or *native*, thus no changes are needed in the calculations from step 1.

3.  Apply the `memory_initials`:

    -   *\-Xms*: 100% \* 795M = 795M

    -   *\-Xmx*: 795M

    -   *\-XX:MetaspaceSize*: 50% \* 70M = 35M

    -   *\-XX:MaxMetaspaceSize*: 70M

    -   *\-Xss*: stack / estimated\_number\_of\_threads = 53 / 51.2 = 1060K



**Related Information**  


[Memory Calculator V2](memory-calculator-v2-8eef959.md)

