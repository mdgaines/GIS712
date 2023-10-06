## Download and Install Python API

Follow instructions below or at this [link](https://developers.google.com/earth-engine/guides/python_install-conda#install_api)

`conda` install:
<ol>
<li>Make a conda environment for GEE and activate it (or activate environment you wish to use).</li>

`conda env create --file=ee.yml` [optional - if you're creating a new env from the yml and get a "Kernel died with exit code 1" error, try running `conda install ipykernel --update-deps --force-reinstall` and then restarting the kernel]

`conda activate [ee]`

<li>Sign up for an individual GEE account (one time only).</li>

Sign up [here](https://signup.earthengine.google.com/) or follow the **Individual signup** instructions [here](https://developers.google.com/earth-engine/guides/access#individual-signup).

Sign up using your **NCSU** email account.

<!-- <li>Install Python API using conda-forge.</li>

*If you create your environment from the ee.yml file provided, move on to Step 3.*

`conda install -c conda-forge earthengine-api`

From the GEE instructions: "You will be asked to confirm the installation of the API and its dependencies. After confirming, conda will download and install the dependencies." -->


<li>Authenticate your Google account (one time only).</li>

**This authentication flow requires installing the Google Cloud Command Line Interface (gcloud) on a machine that has a web browser.**

  <ol type="a">
    <li>Check if `gcloud` is installed on your machine </li>
    <ol type="i">
      <li> run `gcloud help` </li>
      <li>if it is not installed, you will need to download and install `gcloud` following the instructions below</li>
    </ol>
  
---

#### <li> Install `gcloud` (From the online instructions) </li>

Click on the arrow next to the type of computer and follow the instructions (online instructions [here](https://cloud.google.com/sdk/docs/install))


<details>
<summary>Windows </summary>
<br>
The Google Cloud CLI works on Windows 8.1 and later and Windows Server 2012 and later.

1. Download the [Google Cloud CLI installer](https://cloud.google.com/sdk/docs/install).

Alternatively, open a PowerShell terminal and run the following PowerShell commands:

```
>>> (New-Object Net.WebClient).DownloadFile("https://dl.google.com/dl/cloudsdk/channels/rapid/GoogleCloudSDKInstaller.exe", "$env:Temp\GoogleCloudSDKInstaller.exe")

>>> & $env:Temp\GoogleCloudSDKInstaller.exe
    
```

2. Launch the installer and follow the prompts. The installer is signed by Google LLC.

3. Cloud SDK requires Python; supported versions are Python 3 (3.5 to 3.9). By default, the Windows version of Cloud SDK comes bundled with Python 3. To use Cloud SDK, your operating system must be able to run a supported version of Python.

The installer installs all necessary dependencies, including the needed Python version. While Cloud SDK installs and manages Python 3 by default, you can use an existing Python installation if necessary by **unchecking** the option to Install Bundled Python. See [gcloud topic startup](https://cloud.google.com/sdk/gcloud/reference/topic/startup) to learn how to use an existing Python installation.

4. After installation is complete, the installer gives you the option to create Start Menu and Desktop shortcuts, start the Google Cloud CLI shell, and configure the gcloud CLI. Make sure that you leave the options to start the shell and configure your installation selected. The installer starts a terminal window and runs the **`gcloud init`** command.

5. The default installation doesn't include the App Engine extensions required to deploy an application using `gcloud` commands. These components can be installed using the [gcloud CLI component manager](https://cloud.google.com/sdk/docs/managing-components).

**Troubleshooting tips:**
* If your installation is unsuccessful due to the `find` command not being recognized, ensure your `PATH` environment variable is set to include the folder containing `find`. Usually, this is `C:\WINDOWS\system32;`.
* If you uninstalled the gcloud CLI, you must reboot your system before installing the gcloud CLI again.
* If unzipping fails, run the installer as an administrator.

6. Sign into gcloud with your **NCSU** email.

  - Do not create a new project

7. Close all the terminals that are open (SDK and Anaconda).

</details>

<p>
<p>

<details>
<summary>macOS </summary>
<br>

1. Confirm that you have a supported version of Python:

    * To check your current Python version, run `python3 -V` or `python -V`. Supported versions are Python 3 (3.5 to 3.9).
    * For Cloud SDK release version 352.0.0 and above, the main install script offers to install CPython's Python 3.7 on Intel-based Macs.
    * For more information on how to choose and configure your Python interpreter, refer to [gcloud topic startup](https://cloud.google.com/sdk/gcloud/reference/topic/startup).

    **You should have Python 3.9 installed and active, because that is what we set up in our ee.yml file.**

2. Download one of the following:

| **Platform** | **Package** | **Size** | **SHA256 Checksum** |
| --- | --- | --- | --- |
| macOS 64-bit (x86_64) | [google-cloud-cli-425.0.0-darwin-x86_64.tar.gz](https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-425.0.0-darwin-x86_64.tar.gz) | 124.8 MB |b1f0731482243a08ffc2c362092871ab0fa2bd0db1bc68f12ae0c6bf284a0b1c |
| macOS 64-bit (ARM64, Apple M1 silicon) | [google-cloud-cli-425.0.0-darwin-arm.tar.gz](https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-425.0.0-darwin-arm.tar.gz) | 121.7 MB | 0871269d6f7314b2c8f32afcddcc1054d62a108cb89c80a0cdee9f4542d0cece |
| macOS 32-bit (x86) | [google-cloud-cli-425.0.0-darwin-x86.tar.gz](https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-425.0.0-darwin-x86.tar.gz) | 104.5 MB | 0b8fb0801374bdaaac641beb2da28acda7001fad498bab0db6742a3610c0f610 |


**NOTE:** To determine your machine hardware name, run `uname -m` from a command line.

3. Extract the archive to any location on your file system (preferably your Home directory **not in your Downloads folder**, ex: `C:/user/Home`). On macOS, this can be achieved by opening the downloaded `.tar.gz` archive file in the preferred location.

To replace an existing installation, remove the existing `google-cloud-sdk` directory and then extract the archive to the same location.

4. (Optional) Use the install script to add gcloud CLI tools to your `PATH`. You can also opt-in to command-completion for your shell, [usage statistics collection](https://cloud.google.com/sdk/docs/usage-statistics), and install Python 3.7.

5. From the root of the folder you extracted in the last step (ex: change directories to get to the directory where we opened the .tar.gz file by running  `>>> cd C:/user/Home`) run the script using this command:

`>>> ./google-cloud-sdk/install.sh `

  - This can also be done non-interactively (for example, using a script) by providing preferences as flags. To describe the available flags, run:

`./google-cloud-sdk/install.sh --help`

  - To run the install script with screen reader mode on:

`./google-cloud-sdk/install.sh --screen-reader=true`

6. **Close the terminal and open a new terminal so that the changes take effect.**

7. Activate your ee environment.

8. Initialize the gcloud CLI by runnig **`gcloud init`**:

`>>> ./google-cloud-sdk/bin/gcloud init`

9. Sign into gcloud with your **NCSU** email.

  - Do not create a new project

10. Optional. Install additional components using the [component manager](https://cloud.google.com/sdk/docs/managing-components).

</details>

---

</ol>

<p>
<p>

<li> Open Local Machine Terminal (Anaconda) </li>

  * run `earthengine authenticate`
  * The command output will indicate that **gcloud** is being used to fetch credentials.
  * A browser window will open to an account selection page.

<p>
<ol type="a">
<li> Browser: Account Selection</li>
  <ol type="i">
    <li>Select the account you want to use for authentication. (NCSU gmail account)</li>
  </ol>
<p>

<li> Browser: Consent Screen</li>
    <ol type="i">
    <li>Indicate if you are willing to grant the requested scopes and click "Allow".</li>
  </ol>
<p>

<li> Browser: Confirmation Screen</li>
 <ol type="i">
    <li>The browser will show a page confirming that you are authenticated, and the `earthengine authenticate` command in your terminal window will report "Successfully saved authorization token."</li>
  </ol>
<p>
</ol>
<p>

<!-- * Proceed with initialization. -->

<!-- #### *If you create your environment from the ee.yml file provided, move on to Step 6.*

<li>Install folium module</li>

`conda install -c conda-forge folium`

We will use this to create some dynamic maps.

<li>Install ipykernel and pandas (if not already installed)</li>

`conda install pandas`

`conda install -c conda-forge ipykernel` -->

<li>Close your terminals, restart VS Code, and re-activate your ee environment.

<p>

<li>Open the introGEE_API.ipynb and test out the ee module!</li>

**Note:** Be sure ipykernel is installed/updated.

</ol>