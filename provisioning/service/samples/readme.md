# Samples for the Azure IoT Device Provisioning Service SDK for Node.js

This file can be found in https://github.com/Azure/azure-iot-sdk-node/tree/main/provisioning/service/samples

This folder contains simple samples showing how to use the various features of the Microsoft Azure IoT Device Provisioning Service from an application running JavaScript code.

## List of samples

* Create a simple IndividualEnrollment object based on TPM.
   *  [create_individual_tpm_enrollment.js][create-individual-tpm-enrollment]
* Create a simple IndividualEnrollment object based on x509 certificate.
   *  [create_individual_x509_enrollment.js][create-individual-x509-enrollment]
* Create a simple EnrollmentGroup object.
   *  [create_enrollment_group.js][create-enrollment-group]
* Create a couple of IndividualEnrollments and delete them.
   *  [create_delete.js][create-delete]
* Create queries for IndividualEnrollments, EnrollmentGroups and DeviceRegistrationStates that belong to an EnrollmentGroup.
   *  [query.js][query-link]
* Perform BulkEnrollmentOperations to do various CRUD operations.
   *  [run_bulk_operation.js][run-bulk-operation]


## How to run the samples


In order to run the device samples you will first need the following prerequisites:
* Node.js v4 or above on your target device. (Check out [Nodejs.org](https://nodejs.org/) for more info)
* [Setup Azure IoT Device Provisioning ][lnk-setup-iot-provisioning] Stop before executing the the Create and provision a simulated device section.  The samples below will perform these steps.

### Using the x509 individual enrollment example
To generate a x509 certificate to run the individual enrollment of a device with x509 you need to create one. See [create-certificate-for-individual-enrollment].

### Using the TPM  individual enrollmentexample
The following is an endorsement key, used for TPM.  It has been generated by a simulator and as it has no corresponding private portion, is only useful as an input to these examples.

AToAAQALAAMAsgAgg3GXZ0SEs/gakMyNRqXXJP1S124GUgtk8qHaGzMUaaoABgCAAEMAEAgAAAAAAAEAxsj2gUScTk1UjuioeTlfGYZrrimExB+bScH75adUMRIi2UOMxG1kw4y+9RW/IVoMl4e620VxZad0ARX2gUqVjYO7KPVt3dyKhZS3dkcvfBisBhP1XH9B33VqHG9SHnbnQXdBUaCgKAfxome8UmBKfe+naTsE5fkvjb/do3/dD6l4sGBwFCnKRdln4XpM03zLpoHFao8zOwt8l/uP3qUIxmCYv9A7m69Ms+5/pCkTu/rK4mRDsfhZ0QLfbzVI6zQFOKF/rwsfBtFeWlWtcuJMKlXdD8TXWElTzgh7JS4qhFzreL0c1mI0GCj+Aws0usZh7dLIVPnlgZcBhgy1SSDQMQ==


Get the following files from the current folder:
* [package.json][package-json]
* **__sample_file.js__** (where **__sample_file.js__** is one of the files listed above and available in this folder)

Place the files in the folder of your choice on the target machine/device then go through the following steps:

* From a shell or Node.js command prompt, navigate to the folder where you placed the sample files. For creating an IndividualEnrollment do:

```
$ npm install
$ node create_individual_enrollment.js "<the connection string for the Device Provisioning instance enclosed in quotes>" "<an endorsement key in quotes>"
```


* For creating an EnrollmentGroup:
 
If you already have a PEM or CER file then simply give the file name below on the command line "node create_enrollment_groupd.js ...".  If you need to create a PEM file there are command scripts in this [directory](https://github.com/Azure/azure-iot-sdk-c/tree/master/tools/CACertificates) that could be useful FOR TESTING.  Please see the md file in that directory [C SDK cert tools overview.](https://github.com/Azure/azure-iot-sdk-c/blob/master/tools/CACertificates/CACertificateOverview.md)

```
$ npm install
$ node create_enrollment_group.js "<the connection string for the Device Provisioning instance enclosed in quotes>" "<The name of a file containing a pem or cer representation of a signing certificate>"
```

* The other samples simply require the connection string:

```
$ npm install
$ node create_delete.js "<the connection string for the Device Provisioning instance enclosed in quotes>"
```

* In order to monitor the results of running the sample, use the portal for the Device Provisioning Service which can display group or individual enrollments.


## Read More
For more information on how to use this library refer to the documents below:
- [Prepare your node.js development environment][node-devbox-setup]
- [Setup IoT Hub][lnk-setup-iot-hub]
- [Provision devices][lnk-manage-iot-hub]
- [Node API reference][node-api-reference]
- [Device Provisioning Service Concepts][dps-service-concepts]

[lnk-setup-iot-provisioning]: https://docs.microsoft.com/en-us/azure/iot-dps/quick-setup-auto-provision
[lnk-setup-iot-hub]: https://aka.ms/howtocreateazureiothub
[lnk-manage-iot-hub]: https://aka.ms/manageiothub
[node-api-reference]: https://docs.microsoft.com/en-us/javascript/api/azure-iot-device/
[node-devbox-setup]: ../../doc/node-devbox-setup.md
[create-individual-tpm-enrollment]: https://github.com/azure/azure-iot-sdk-node/tree/main/provisioning/service/samples/create_individual_tpm_enrollment.js
[create-individual-x509-enrollment]: https://github.com/azure/azure-iot-sdk-node/tree/main/provisioning/service/samples/create_individual_x509_enrollment.js
[create-enrollment-group]: https://github.com/azure/azure-iot-sdk-node/tree/main/provisioning/service/samples/create_enrollment_group.js
[dps-service-concepts]: https://docs.microsoft.com/en-us/azure/iot-dps/concepts-service
[create-delete]: https://github.com/azure/azure-iot-sdk-node/tree/main/provisioning/service/samples/create_delete.js
[query-link]: https://github.com/azure/azure-iot-sdk-node/tree/main/provisioning/service/samples/query.js
[run-bulk-operation]: https://github.com/azure/azure-iot-sdk-node/tree/main/provisioning/service/samples/query.js
[package-json]: https://github.com/azure/azure-iot-sdk-node/tree/main/provisioning/service/samples/package.json
[create-certificate-for-individual-enrollment]: https://github.com/Azure/azure-iot-sdk-node/tree/main/provisioning/device/samples#creating-x509-device-certificates-for-individual-enrollment
