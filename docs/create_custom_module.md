# Create Custom Module

## create a real estate module
=== "Ubuntu"
    ```zsh
    mkdir local/addons/custom_module
    ```
    ```zsh
    touch local/addons/custom_module/{__init__,__manifest__}.py
    ```

=== "Windows"
    ```zsh
    mkdir local/addons/custom_module
    ```
    ```zsh
    touch local/addons/custom_module/{__init__,__manifest__}.py
    ```


```py title="__manifest__.py" linenums="1" hl_lines="8 9"
{
    "name":"Custom Module",
    "author":"Multi Academy",
    "category":"Human Resources",
    "application":True,
    "depends":["base"],
    "data":[
        'views/menu.xml',
        'views/menu.xml',
    ]
}
```