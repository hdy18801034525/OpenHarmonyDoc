# HiSysEvent Logging Configuration<a name="EN-US_TOPIC_0000001080478132"></a>

-   [Overview](#section315316685115)
    -   [Basic Concepts](#section123181432175143)
        -   [Constraints](#section123181432175114)
-   [Writing a YAML File](#section123181432175113)
    -   [Writing Rules](#section123181432175133)
        -   [Example](#section123181432175123)
-   [Verifying the YAML File](#section123181432175115)
    -   [Configuring the YAML File Path](#section123181432175135)
    -   [Compiling the YAML File](#section123181432175137)
    -   [Logging and Querying Events](#section123181432175139)

## Overview<a name="section315316685115"></a>

If HiSysEvent logging is required for a component, you need to define a YAML file and [configure the YAML file path](#section123181432175135) in the **bundle.js** file. During compilation, the OpenHarmony compilation framework will use the Python compilation script to parse and verify all the YAML files configured in the **bundle.js** file. On completion, the compilation framework will summarize the configuration information in the YAML files and convert the information into a JSON file named **hisysevent.def**. After that, the compilation framework will put the JSON file to a specified path as the basis for the system to determine whether to log system events.

### Basic Concepts<a name="section123181432175143"></a>

Understanding the following concepts would be helpful for you in configuring HiSysEvent logging.

- Event domain
  Represents the domain to which an event belongs. It is specified by the **domain** field in the YAML file. For details, see [domain](#section123181432175123) in the example YAML file.

- Event name
  Indicates the events in an event domain. For details, see [EVENT\_NAMEA/EVENT\_NAMEB](#section123181432175123) in the example YAML file.

- Parameter
  Defines the key values in an event name. For details, see [__BASE/NAME1/NAME2](#section123181432175123) in the example YAML file.


### Constraints<a name="section123181432175114"></a>

- Each YAML file can contain only one event domain, and the domain name cannot be the same as that defined in other YAML files.

- Zero or more event names can be defined for one event domain. The event names in the same event domain must be unique.

- Multiple parameters can be defined for one event name. The parameters in the same event name must be unique. There must be one and only one parameter named **\__BASE** in each event name. See Table 1 for the fields of this parameter and Table 2 for the fields of other custom parameters.

  **Table 1** Fields in the \__BASE parameter

  | Field| Description|
  | ----- | ----- |
  | type | Indicates the type of the event. This field is mandatory. <br><br>Value:<ul><li>**FAULT**: fault </li><li>**STATISTIC**: statistics </li><li>**SECURITY**: security </li><li>**BEHAVIOR**: user behavior</li></ul> |
  | level | Indicates the level of the event. This field is mandatory. <br><br>Value: <ul><li>**CRITICAL**: critical </li><li>**MINOR**: minor</li></ul> |
  | tag | Indicates the tag of the event. This field is mandatory. <br><br>Rule:<ul><li>You can define a maximum of five tags,separated with a space. </li><li>A single tag can contain a maximum of 16 characters, including a to z, A to Z, and 0 to 9.</li></ul>|
  | desc | Describes the event name. This field is mandatory. <br><br>Rule:<ul><li>The description contains 3 to 128 characters, including a to z, A to Z, 0 to 9, and underscores (&#95;).</li></ul>|

  **Table 2** Description of custom parameters

  | Field| Description|
  | ----- | ----- |
  | type | Indicates the type of a parameter. This field is mandatory. <br><br>Value: <ul><li>BOOL</li><li>UINT8</li><li>UINT16</li><li>INT32</li><li>UINT32</li><li>UINT64</li><li>FLOAT</li><li>DOUBLE</li><li>STRING</li></ul>|
  | arrsize | Specifies the length of the parameter of the array type. This field is optional. <br><br>Value range: <ul><li>1-100</li></ul>|
  | desc | Describes the parameter. This field is mandatory. <br><br>Rule:<ul><li>The description contains 3 to 128 characters, including a to z, A to Z, 0 to 9, and underscores (&#95;).</li></ul>|

## Writing a YAML File<a name="section123181432175113"></a>

### Writing Rules<a name="section123181432175133"></a>

-   Event domain naming rules:
    -   The name must start with a letter and can contain only uppercase letters, digits, and underscores (&#95;).
    -   The name contains 1 to 16 characters.
-   Event naming rules:
    -   The name must start with a letter and can contain only uppercase letters, digits, and underscores (&#95;).
    -   The name contains 1 to 32 characters.
    -   The number of internal event names in an event domain cannot exceed 4096.
-   Parameter naming rules:
    -   The name must start with a letter and can contain only uppercase letters, digits, and underscores (&#95;).
    -   The name contains 1 to 32 characters.
    -   The number of parameters in an event domain cannot exceed 128.

### Example<a name="section123181432175123"></a>

-   In the example YAML file, the event domain name is **MODULEA**. The event domain contains two events named **EVENT\_NAMEA** and **EVENT\_NAMEB**.
-   **EVENT\_NAMEA** is defined as a critical event of the fault type. The event contains the **NAME1** parameter of the string type, the **NAME2** parameter of the string type, and the **NAME3** parameter of the unsigned short integer type. Therefore, you can perform [real-time subscription](subsys-dfx-hisysevent-listening.md) to the event based on the event domain **MODULEA** and event name **EVENT\_NAMEA**.
-   **EVENT\_NAMEB** is defined as a general event of the statistics type. The event contains the **NAME1** parameter of the unsigned short integer type and the **NAME2** parameter of the integer type. Because two event tags named **tag1** and **tag2** are defined for **EVENT\_NAMEB** in the **\__BASE** parameter, you can perform [real-time subscription](subsys-dfx-hisysevent-read.md) to the event based on the event domain **MODULEA** and event name **EVENT\_NAMEB**, or based on the event tag.

    ```
    ##########################################
    # HiSysEvent definition for MODULEA
    ##########################################

    domain: MODULEA

    EVENT_NAMEA:
        __BASE: {type: FAULT, level: CRITICAL, desc: event name a}
        NAME1: {type: STRING, desc: name1}
        NAME2: {type: STRING, desc: name2}
        NAME3: {type: UINT16, desc: name3}

    EVENT_NAMEB:
        __BASE: {type: STATISTIC, level: MINOR, tag: tag1 tag2, desc: event name b}
        NAME1: {type: UINT16, desc: name1}
        NAME2: {type: INT32, desc: name2}
    ```

## Verifying the YAML File<a name="section123181432175115"></a>

### Configuring the YAML File Path<a name="section123181432175135"></a>

In the **bundle.js** file, use the ```hisysevent_config``` attribute to specify the YAML file path.

```
{
    "name": "@ohos/moduel_a",
    "description": "module a",
    "version": "3.1",
    "license": "Apache License 2.0",
    "publishAs": "code-segment",
    "segment": {
        "destPath": "moduel_a_path"
    },
    "dirs": {},
    "scripts": {},
    "component": {
        "name": "hisysevent_native",
        "subsystem": "hiviewdfx",
        "adapted_system_type": [
            "standard"
        ],
        "rom": "",
        "ram": "",
        "hisysevent_config": [
            "//moduel_a_path/yaml_file1.yaml",
            "//moduel_a_path/yaml_file2.yaml"
        ],
        "deps": {
            "components": [
                "hilog_native",
                "hitrace_native",
                "ipc",
                "safwk",
                "samgr_standard",
                "utils_base"
            ],
            "third_party": []
        },
        "build": {
        }
    }
}
```

>![](../public_sys-resources/icon-note.gif) **Note:**
>The YAML file can be placed in any directory of the component project as needed. You only need to specify the path in the **bundle.js** file.

### Compiling the YAML File<a name="section123181432175137"></a>

-   Perform full compilation.

    -   During full compilation of the system, the configuration in the YAML files of all components are summarized. After the compilation is complete, the **hisysevent.def** file will be generated in the specified directory.

    ```
    cd absolute path of the project's root directory
    ./build --product-name <product name>
    ```

    -   To obtain the **hisysevent.def** file generated after full compilation, run the following command:

    ```
    cd absolute path of the project's root directory
    find out -name hisysevent.def -type f
    ```

-   Single-file compilation:

    You can also compile the YAML file of a single component by running the following commands:

    ```
    cd absolute path of the project's root directory
    ./build/ohos/hisysevent/gen_def_from_all_yaml.py --yaml-list <yaml file list> --def-path <file store directory>
    ```

  **Table 3** Parameters for single-file compilation

  | Parameter| Description|
  | ------ | ------ |
  | --yaml-list | Specifies the paths of the YAML files to be compiled. If there are multiple YAML file paths, separate each of them with a space.|
  | --def-path | Specifies the path of the **hisysevent.def** file generated after compilation.|

### Logging and Querying Events<a name="section123181432175139"></a>

1.  Push the **hisysevent.def** file to the **/system/etc/hiview/** directory of the device by using the [hdc_std tool](subsys-toolchain-hdc-guide.md).

2.  Trigger logging of the custom system events in the YAML file. Then, run [hisysevent -l](subsys-dfx-hisysevent-tool.md) to query historical system events to find out if the logging of the custom system events is successful.