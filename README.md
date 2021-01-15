# What is this?

This is the official *ncode* agent release for GNU/Linux.
With the `ncode` agent one can connect and profile local CSV data files in order to monitor and generate alerts whenever the data changes.
No real data is transferred to the `ncode` cloud.


For further information about License, Terms and Privacy policy, do refer to the official website [ncode.ai](https://ncode.ai)
We are currently accepting only users by invitation. If you would like to give our platform a try, please send a request to hello@ncode.ai


# Getting started

The agent is distributed in executable format (until code release). Please download the version for your operating system and get started.
With the executable saved to your local machine you can extract metadata from your local data assets, login and access the official ncode API and interact with it.

| Operating System | ver. 0.1      | Description     |
| -------------    |:-------------:| ---------------:|
| GNU/Linux        | [download](https://github.com/fgadaleta/ncode-agent/releases/download/v0.1-alpha/ncode-linux)        | v0.1-alpha pre-release |
| Mac OS           | [download](https://github.com/fgadaleta/ncode-agent/releases/download/v0.1-alpha/ncode-macos)        | v0.1-alpha pre-release |
| MS Windows       | NA          |  NA  |

For the sake of simplicity, from here on we refer to the ncode executable as `./ncode` for both operating systems.

The official CLI includes a minimal help documentation via `./ncode --help`  


## Configuration

Downloaded the `ncode` agent for your OS.

The first time the `ncode` agent is ran, a directory `.ncode` will be created under the `HOME` path. 
In such folder a sample configuration file will be created. Please do copy it to `configuration.toml` with the correct `username` and `password` provided to you via email.

Change permissions of the executable so that you can launch it from the terminal
From the folder where the ncode agent is stored, type 

`chmod a+x ncode-linux`


## Login

The first time you execute the agent with `./ncode login`, a configuration folder will be created under `~/.ncode`
Please copy the sample configuration file to `configuration.toml` under the same folder.

Once the configuration file has been set, it is possible to login directly from the CLI.

```bash
$ ./ncode login
```

## Profile local data

In order to monitor local data at `mypath/mydata.csv`, one needs to profile to extract metadata first. 
The command to extract metadata and publish to the private space on the ncode cloud is 

```bash
$ ./ncode profile --input mypath/mydata.csv --publish

```

## List all published data assets

In order to list all the published metadata to ncode, run command

```bash
$ ./ncode data --all
```

## List one specific data asset

In order to view the metadata of a particular data asset, e.g. with specific `id=0x1234`, type

```bash
$ ./ncode data --id 0x1234
```

## Profile published data

In order to profile the same data asset multiple times, type the same command as above, specifing the full/relative path.
The data owner has to re-profile the data every time the original data changes. 
The new metadata will be compared in the cloud to the most recent profile and alerts will be generated.

```bash
$ ./ncode profile --input mypath/mydata.csv --publish

```

At this point, if changes are detected a series of alerts will be automatically generated for you and forwarded directly to your valid email address.
It is also possible to interact with such alerts (e.g. view all alerts, view specific alerts by id, delete alerts).

## List all alerts

Alerts referring to a specific data asset with `id=0x1234` can be viewed with

```bash
$ ./ncode alerts --data 0x1234
```

### Types of generated alerts

This release contains the following alerts that are automatically generated:

* column name
* min, max, mean, standard deviation 
* number of elements
* number of unique elements
* number of null elements
* histogram
* statistical drift 


## Delete all alerts 

After listing alerts for a specific data asset, it is possible to delete them with `--delete` flag like below

```bash
$ ./ncode alerts --data 0x1234 --delete
```


# Found an Issue? Let us know

If you find an issue that requires a fix, please use the Issue system on the [GitHub repository](https://github.com/fgadaleta/ncode-agent/issues)
