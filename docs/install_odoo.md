## Project Structure

=== "Odoo 16 Community"

    ``` mermaid
    graph LR
    A[odoo-dev] --> B[conf];
    A --> C[src];
    A --> D[local];
    A --> E[venv];

    B --> F[odoo16c.conf]

    C --> J[odoo16c]
    J --> K[odoo-bin]
    K --> S

    J --> L[addons]
    L --> F

    D --> P[odoo16c-custom-addons]
    P --> F

    E --> R[activate]
    R --> S

    F --> S[Runner]
    
    ```

=== "Odoo 16 Enterprise"

    ``` mermaid
    graph LR
    A[odoo-dev] --> B[conf];
    A --> C[src];
    A --> D[local];
    A --> E[venv];

    B --> F[odoo16e.conf]

    C --> J[odoo16e]
    J --> K[odoo-bin]
    K --> S

    J --> L[addons]
    L --> F

    D --> P[odoo16e-custom-addons]
    P --> F

    E --> R[activate]
    R --> S

    F --> S[Runner]
    
    ```
=== "Both"

    ``` mermaid
    graph LR
    A[odoo-dev] --> B[conf];
    A --> C[src];
    A --> D[local];
    A --> E[venv];

    B --> L[odoo16c.conf]
    B --> M[odoo16e.conf]

    C --> F[odoo16c]
    F --> G[odoo-bin]
    F --> H[addons]

    C --> I[odoo16e]
    I --> J[odoo-bin]
    I --> K[addons]

    D --> O[custom-addons]
    E --> P[activate]

    L --> Q[odoo-bin -c odoo16c.conf]
    G --> Q
    H --> L
    O --> L

    M --> R[odoo-bin -c odoo16e.conf]
    J --> R
    K --> M
    ```

## create project directory

=== "Ubuntu"
    ```zsh
    mkdir src local conf
    ```
=== "Windows"
    ```zsh
    mkdir src local conf
    ```
## Clone Git Repo

=== "Ubuntu"

    ```zsh
    git clone https://github.com/odoo/odoo.git --branch 16.0 --single-branch src/odoo16c
    ```

=== "Windows"

    ```zsh
    git clone https://github.com/odoo/odoo.git --branch 16.0 --single-branch src/odoo16c
    ```

## Install PostgreSQL

=== "Ubuntu"

    ```zsh
    sudo apt-get install postgresql
    ```

    ```zsh
    sudo su - postgres
    ```

    ```zsh
    createuser --createdb --username postgres --no-createrole --no-superuser --pwprompt <user-name>
    ```

    ```zsh
    psql
    ```

    ```zsh
    ALTER USER odoo15 WITH SUPERUSER;
    ```

=== "Windows"

    Download from - [`postgresql.org`](https://www.postgresql.org/download/windows/)

## Install Wkhtmltopdf

=== "Ubuntu"

    ```zsh
    sudo apt-get install wkhtmltopdf
    ```

=== "Windows"

    Download from - [`wkhtmltopdf.org`](https://wkhtmltopdf.org/downloads.html)

## Create virtual environment & Activate

=== "Ubuntu"

    ```zsh
    python3 -m venv venv
    ```
    ```zsh
    source venv/bin/activate
    ```

    `(venv) >`

=== "Windows"

    ```cmd
    python -m venv venv
    ```

    ```cmd
    cd venv/bin/ && activate
    ```

    `(venv) >`

## Install Requirements

=== "Ubuntu"

    ```zsh
    pip3 install -r requirements.txt
    ```

=== "Windows"

    ```cmd
    pip install -r requirements.txt
    ```

if you have package installing error remove package of version from - `requirements.txt`

## Fixed

### psycopg2

=== "Ubuntu"
    ```zsh
    pip3 install psycopg2-binary
    ```

    ```zsh
    sudo apt install build-essential libpq-dev python3-dev
    ```

    ```zsh
    pip3 install psycopg2
    ```

=== "Windows"

    ```zsh
    pip install psycopg2-binary
    ```

## Run Odoo

=== "Ubuntu"
    ```zsh
    python3 src/odoo16c/odoo-bin -c conf/odoo16c.conf
    ```

=== "Windows"

    ```zsh
    python src/odoo16c/odoo-bin -c conf/odoo16c.conf
    ```
