# Ansys

Ansys Mechanical finite element analysis software is used to simulate computer
models of structures, electronics, or machine components for analyzing
strength, toughness, elasticity, temperature distribution, electromagnetism,
fluid flow, and other attributes.

It includes software such as Fluent and CFX.

Versions available: 17.2/18.1/19.1/19.2

URL: [ansys.com](https://ansys.com)

## Licensing

Ansys is licensed software, available to users with a departmental license.

## Usage

### Setup

This setup only needs to be done once.

````{toggle}

  The license is obtained by setting the ANSYSLMD_LICENSE_FILE variable. To set
  it in bash do:
  ```bash
  $ export ANSYSLMD_LICENSE_FILE=<port>@<host>
  ```
  If accessing for the first time, there is an additional step (see the next
  section on this page) required to choose whether you are using commercial or
  academic licenses. To get the values of `<port>@<host>` specific to your
  group/department please contact the Client IT Team via Service Now.

  Before running the Ansys module for the first time, there is a per-user
  setting that chooses whether commercial (default) or academic licenses should
  be used.

  For research purposes you should normally be using the academic licenses,
  unless you are untertaking commercially funded research.

  Check with your supervisor if you need clarification on this.

  You will need a SSH connection with X-forwarding enabled to configure this
  setting.  Refer to the [getting started guide](../../getting_started/logon).

  If you have not already done so, set the license server and port:
  ```bash
  $ export ANSYSLMD_LICENSE_FILE=<port>@<host>
  ```
  Next, ensure that you have the Ansys module loaded for the particular version
  you wish to configure its licenses, e.g.:

  ```bash
  $ module add ansys/19.2
  ```
  for Ansys version 19.2

  You now need to launch the license administration interface. The simplest way
  to do this is to start cfx:

  ```bash
  $ cfx5
  ```
  and select Tools/Ansys client Licensing Utility from the menu.

  This will present you with the following window:

  ![Configuring a license for Ansys using the license manager.](../../assets/img/applications/ansys_license.jpg)
  Select “set license preferences for user abcxyz”

  In the next window, select the product you wish to configure (e.g. 12.1)

  ![Selecting the right license preferences.](../../assets/img/applications/ansys_license1.jpg)
  In the next window that appears, select the radio button that says Use
  academic licenses:

  ![Finally select the academic license option.](../../assets/img/applications/ansys_license3.jpg)
  Select OK, then exit the license manager.

  This will configure Ansys (both Fluent and CFX) to use Academic licenses for
  all future use.
````

#### Fluent

[Additional guidance on running Fluent](ansys/fluent)

#### CFX

[Additional guidance on running CFX](ansys/cfx)

#### Chemkin

[Additional guidance on running Chemkin](ansys/chemkin)
