# SWIFT4Corporates for the Ab Initio Metadata>Hub

This repository contains the Ab Initio Metadata>Hub SWIFT4Corporates Release initially for NACHA.

The following Messages, their Business Components and Codeset are included

	camt.052.001.02 BankToCustomerAccountReportV02
	camt.054.001.02 BankToCustomerDebitCreditNotificationV02
	camt.053.001.02 BankToCustomerStatementV02
	pain.001.001.03 CustomerCreditTransferInitiationV03
	pain.008.001.02 CustomerDirectDebitInitiationV02
	pain.002.001.03 CustomerPaymentStatusReportV03

You'll end up with a comprehensive set of metadata, with a fully populated Business Dictionary, Reference Data, Logical Models, System and Applications, Datasets and Mapping Specs.

## How to deploy

Download the repository using Git.

### Import the Ab Initio Metadata>Hub Rules

	dotin your Metadata>Hub Profile
	cd rules
	mh-import rule save Enrich_BizTerm_Golden_DataElem_Import.rule
	mh-import rule save Standard_Excel_Import_DELETE_OBJECT.rule
	mh-import rule save Standard_MSLI_ENRICH_OBJECT_for_BizTerm-1.rule
	mh-import rule save Standard_MSLI_ENRICH_OBJECT_for_LogAttr-1.rule
	mh-import rule save Standard_MSLI_Import_DELETE_OBJECT.rule

### Import the Ab Initio Metadata>Hub Feeds

	dotin your Metadata>Hub Profile
	cd feeds
	for feedName in *
	do
		mh-import feed save $feedName
	done


### Add a site parameter called MHHUB_ENV_DATA_ROOT

The use of the site parameter called MHUB_ENV_DATA_ROOT is for parameterisation of the location of MSLI files  

	mh-import site-parameters add -name MHHUB_ENV_DATA_ROOT -value /your/location/on/disk/here 

### Run the feed import script

Witin the run directory is a script called run-me.ksh that will load, submit and approve the feeds in the correct order.
