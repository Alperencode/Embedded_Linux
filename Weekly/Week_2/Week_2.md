# Week 2

## Week 2 Plan

- <u>Python AT-Library</u> 
  - [Set-up](#set-up)
  - [Develop](#develop)
  - [To-do](#to-do)
  - [Notes](#notes)
  - [Sample Images and Code Snippets](#samples)

## Python AT Library

<hr>

## Set-up

First of all I configured my workspace

- Set up SSH extension for VSCode
- Create `AT-Lib` repository
- Add `AT-Lib` as submodule to this repository
- Create main directory structure for `AT-Lib`
  - Initialize tests and source directories
  - Add workflow folder for GitHub actions
    - Add linting and tests actions
    - Sample image [here](#workflow-snippet)

<br><hr>

## Develop

First, I've started to build class named `ATLIB` which will allow following operations (*can be updated later*)
- Constructor for creating Serial class object ✔️
- Find valid port ✔️
  - Code snippet [here](#get-port-function)
- Open serial connection
- Send at command
- Get response

<br><hr>

## To-do

- Remove `pytest` comment line in [workflow](https://github.com/Alperencode/AT-Lib/blob/a8e9a2ebcf66b15230fe635df1f1a7c2c8d9ddf5/.github/workflows/python-app.yml#L43) after adding tests.

<br><hr>

## Notes

- To recursively update submodule 
  - ```$ git submodule update --recursive --remote```
- Linux  directory structure:
  - `/dev`: **Consists of files that represent devices that are attached to the local system.**
  - `/bin`: Contains essential executable files that are required for basic system functionality.
  - `/etc`: Stores system configuration files, Whenever any new application is installed, the configuration files are always kept here by default.
  - `/home`: houses user-specific files and directories.


##### Sources

- [Understanding the /dev Directory in Linux](https://www.baeldung.com/linux/dev-directory)
- [Dev Directory](https://dev.to/softwaresennin/linux-directory-structure-simplified-a-comprehensive-guide-3012)
- pySerial Serial class [docs](https://pyserial.readthedocs.io/en/latest/pyserial_api.html).
- Modem bit settings [here](https://lehman.edu/lehman/depts/depts/langlit/help/setmodem.htm).
- End of AT commands [question](https://stackoverflow.com/questions/13286086/end-of-response-to-an-at-command) ("\r\n").

<br><hr>

## Samples

### Workflow snippet

![Workflow](../../images/Workflow.png)

### Get Port function

```python
    @staticmethod
    def get_port():
        from serial.tools import list_ports

        for port in list_ports.comports():
            if port.product is not None:
                return port.device
```