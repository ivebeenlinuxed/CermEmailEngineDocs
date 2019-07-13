---
title: "Configuring CERM Flows"
keywords: configure
tags: [getting_started, configure]
permalink: configuration.html
summary: Configuring the CERM Flows software
---

{% include note.html content="You must restart the service for changes to take affect" %}

## Setting up CERM Flows

CERM Flows only requires the Global section of the ini file to be configured to run, however in order to begin sending emails, or using the API functionality blocks, you need to setup the relevant sections. We recommend you ALWAYS set the Global and Email settings.

## Add the log table to the CERM database

This table is required, as it will be the main logging point for the software. In future versions this may be added automatically.

```SQL
SET ANSI_NULLS ON
  SET QUOTED_IDENTIFIER ON
  CREATE TABLE flow_log (
	  [Id] [int] IDENTITY(1,1) NOT NULL,
	  [MachineName] [nvarchar](50) NOT NULL,
	  [Logged] [datetime] NOT NULL,
	  [Level] [nvarchar](50) NOT NULL,
	  [Message] [nvarchar](max) NOT NULL,
	  [ClassName] [nvarchar](max) NULL,
	  [Method] [nvarchar](max) NULL,
      [LogType] [nvarchar](50) NOT NULL,
	  [FlowId] [nvarchar](36),
	  [FlowNodeId] [nvarchar](36),
	  [Exception] [nvarchar](max) NULL,
    CONSTRAINT [PK_FlowLog] PRIMARY KEY CLUSTERED ([Id] ASC)
      WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
  ) ON [PRIMARY]
```


## Location of configuration ini file


On a CERM-ENGINE, a registry key HKEY_LOCAL_MACHINE\\SOFTWARE\\wow6432node\\Cerm\\Parameters\\ConfigLocation is used to determine the location of the "Flows.ini" file. This is to ensure that a backup is created as part of the CERM Backup process.

This normally means you will find the config file here:
```
\\CERM-DATA\sqlb00\cfg\Flows.ini
```

If this registry key is not available the configuration file is loaded from:

```
C:\\ProgramData\\Cerm\\Flows.ini
```

## Factory Settings


The default INI file looks like this:

```ini
[Global]
BindAddress=ws://0.0.0.0:9000/
FlowDirectory=\\cerm-data\sqlb00\cfg\Flows
SharedFolder=\\cerm-data\sqlb00\brf\Flows
TemplatesFolder=\\cerm-data\sqlb00\brf\Flows\Templates
UserName=CermUser
Password=cermpass
UserID=100002

[Email]
Server=smtp.office365.com
Authentication=yes
FromAddress=noreply@yourdomain.com
Username=noreply@yourdomain.com
Password=qwertypasword
SSL=587


[REST]
token_url=http://localhost:43002/oauth/token
client_id=5AXXXXXXXXXXXXXXXXFAB
client_secret=test1234
username=cerm
password=1
api_base=http://w2008-ont:43001
```

### Global Configuration

{% include warning.html content="Make sure all the configured directories are available on the server before starting the service." %}

#### BindAddress

This tells the HTML frontend where to find the backend server. Don't touch! If this doesn't stay the same it simply won't work!

#### FlowDirectory

This tells the server where to find the flowcharts that the server should load and run. The system stores each flow as an XML file in this directory.

#### SharedFolder

This tells the server where it is allowed to put temporary files and create directories that all the CERM clients can access. It is used for things like hotfolders, and CERM buttons.

#### TemplatesFolder

To make emailing easy, we make a set of pre-defined HTML templates. These templates can be put into this folder so the software can easily find them

#### UserName

When starting up some CERM applications (like import exe) a CERM login must be provided. Make sure a valid login so the flowchart system is able to login to your CERM installation

#### Password

As above

#### UserID

Depreciated. To be removed.

### Email

The following settings relate to the email system. You should obtain settings from your server administrator. Leave SSL blank in order to not use SSL/TLS security - this is not recommended however.

### REST API

The REST API allows for functions such as automatically quoting, creating products and asking the server for PDF documentation (delivery notes etc).

Please fill in the details, using the API documentation available in the CERM help. The Username and Password must be of a user that is allowed API access. The system will login as this user.

