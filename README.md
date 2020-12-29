# What is this?

This is the official *ncode* agent release for GNU/Linux and MacOS. 
For further information about License, Terms and Privacy policy, do refer to the official website [ncode.ai](https://ncode.ai)
We are currently accepting only users by invitation. If you would like to give our platform a try, please send a request to hello@ncode.ai

# Getting started

The agent is distributed in executable format (until code release). Please download the version for your operating system and get started.
With the executable saved to your local machine you can extract metadata from your local data assets, login and access the official ncode API and interact with it.

| Operating System | ver. 0.1      | Description     |
| -------------    |:-------------:| ---------------:|
| GNU/Linux        | [download](https://test)        | Current release |
| Mac OS           | [download](https://test)        |  NA   |
| MS Windows       | [download]          |  NA  |


The official CLI includes a minimal help documentation via `ncode --help`  


## Configuration

Unzip the file downloaded for your OS.

```
$ unzip ncode-agent
$ cd ncode-agent
```

Edit file `configuration.toml` with the `username` and `password` you have received from the invite.


## Login

Once the configuration file has been set, it is possible to login directly from the CLI.

```
$ ncode login
```

## Profile local data

Assuming one wants to monitor `mypath/mydata.csv`, the command to extract metadata and publish to the private space on the ncode cloud is 

```
ncode profile --data mypath/mydata.csv --publish

```

## List all published data assets

```
ncode data --all
```

## List one specific data asset

In order to print the fields of a particular data assets, e.g. with `id=0x1234`, type

```
ncode data --id 0x1234
```

## Profile published data

In order to profile the same data assets over and over, type the same command as above, specifing the full/relative path.

```
ncode profile --data mypath/mydata.csv --publish

```

At this point, if changes are detected a series of alerts will be automatically generated for you and forwarded directly to your valid email address.
It is also possible to interact with such alerts (list all alerts, list specific alerts, delete alerts).

## List all alerts

Alerts referring to a specific data asset with `id=0x1234` can be listed with

```
ncode alerts --data 0x1234
```

## Delete all alerts 

After listing alerts for a specific data asset, it is possible to delete them with `--delete` flag like below.

```
ncode alerts --data 0x1234 --delete
```


