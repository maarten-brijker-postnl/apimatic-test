
# Getting Started with Postnl-Ecommerce

## Introduction

<div><p><b>PostNL Ecommerce APIs</b></p><p>Explore our technical documentation, test your integration and go live with PostNL service.</p><p><b>Start using PostNL APIs for e-commerce processes</b></p><p>To get to know the PostNL APIs better, read all about it in our <a href='https://developer.postnl.nl/api-overview/'>API overview</a>. Learn everything you need to about our API's before embarking on integration with PostNL.</p><p>To connect to PostNL, you can request an API key via <a href='https://developer.postnl.nl/api-overview/'>Mijn PostNL</a> portal. Choose your APIs and build your integration. Explore our guides, examples, and resources to guide you through each phase of integration and start testing. Ensure that you can make successful test calls towards all endpoints used in the solution.</p><p>Contact our integrations team to have your test calls reviewed and gain access to our API production environment. Once everything is configured and validated, you'll be ready to go live and start using the PostNL service. <br>For help contact us via our support form: <a href='https://developer.postnl.nl/support/form/'>Need help? Submit a case | PostNL</a>.</p></div>


## Building

You must have Python `3 >=3.7, <= 3.11` installed on your system to install and run this SDK. This SDK package depends on other Python packages like pytest, jsonpickle etc. These dependencies are defined in the `requirements.txt` file that comes with the SDK. To resolve these dependencies, you can use the PIP Dependency manager. Install it by following steps at [https://pip.pypa.io/en/stable/installing/](https://pip.pypa.io/en/stable/installing/).

Python and PIP executables should be defined in your PATH. Open command prompt and type `pip --version`. This should display the version of the PIP Dependency Manager installed if your installation was successful and the paths are properly defined.

* Using command line, navigate to the directory containing the generated files (including `requirements.txt`) for the SDK.
* Run the command `pip install -r requirements.txt`. This should install all the required dependencies.

![Building SDK - Step 1](https://apidocs.io/illustration/python?workspaceFolder=Postnlecommerce-Python&step=installDependencies)

## Installation

The following section explains how to use the postnlecommerce library in a new project.

### 1. Open Project in an IDE

Open up a Python IDE like PyCharm. The basic workflow presented here is also applicable if you prefer using a different editor or IDE.

![Open project in PyCharm - Step 1](https://apidocs.io/illustration/python?workspaceFolder=Postnlecommerce-Python&step=pyCharm)

Click on `Open` in PyCharm to browse to your generated SDK directory and then click `OK`.

![Open project in PyCharm - Step 2](https://apidocs.io/illustration/python?workspaceFolder=Postnlecommerce-Python&step=openProject0)

The project files will be displayed in the side bar as follows:

![Open project in PyCharm - Step 3](https://apidocs.io/illustration/python?workspaceFolder=Postnlecommerce-Python&projectName=postnlecommerce&step=openProject1)

### 2. Add a new Test Project

Create a new directory by right clicking on the solution name as shown below:

![Add a new project in PyCharm - Step 1](https://apidocs.io/illustration/python?workspaceFolder=Postnlecommerce-Python&projectName=postnlecommerce&step=createDirectory)

Name the directory as "test".

![Add a new project in PyCharm - Step 2](https://apidocs.io/illustration/python?workspaceFolder=Postnlecommerce-Python&step=nameDirectory)

Add a python file to this project.

![Add a new project in PyCharm - Step 3](https://apidocs.io/illustration/python?workspaceFolder=Postnlecommerce-Python&projectName=postnlecommerce&step=createFile)

Name it "testSDK".

![Add a new project in PyCharm - Step 4](https://apidocs.io/illustration/python?workspaceFolder=Postnlecommerce-Python&projectName=postnlecommerce&step=nameFile)

In your python file you will be required to import the generated python library using the following code lines

```python
from postnlecommerce.postnlecommerce_client import PostnlecommerceClient
```

![Add a new project in PyCharm - Step 5](https://apidocs.io/illustration/python?workspaceFolder=Postnlecommerce-Python&projectName=postnlecommerce&libraryName=postnlecommerce.postnlecommerce_client&className=PostnlecommerceClient&step=projectFiles)

After this you can write code to instantiate an API client object, get a controller object and  make API calls. Sample code is given in the subsequent sections.

### 3. Run the Test Project

To run the file within your test project, right click on your Python file inside your Test project and click on `Run`

![Run Test Project - Step 1](https://apidocs.io/illustration/python?workspaceFolder=Postnlecommerce-Python&projectName=postnlecommerce&libraryName=postnlecommerce.postnlecommerce_client&className=PostnlecommerceClient&step=runProject)

## Test the SDK

You can test the generated SDK and the server with test cases. `unittest` is used as the testing framework and `pytest` is used as the test runner. You can run the tests as follows:

Navigate to the root directory of the SDK and run the following commands

```
pip install -r test-requirements.txt
pytest
```

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| `environment` | `Environment` | The API environment. <br> **Default: `Environment.PRODUCTION_SERVER`** |
| `http_client_instance` | `HttpClient` | The Http Client passed from the sdk user for making requests |
| `override_http_client_configuration` | `bool` | The value which determines to override properties of the passed Http Client from the sdk user |
| `http_call_back` | `HttpCallBack` | The callback value that is invoked before and after an HTTP call is made to an endpoint |
| `timeout` | `float` | The value to use for connection timeout. <br> **Default: 60** |
| `max_retries` | `int` | The number of times to retry an endpoint call if it fails. <br> **Default: 3** |
| `backoff_factor` | `float` | A backoff factor to apply between attempts after the second try. <br> **Default: 2** |
| `retry_statuses` | `Array of int` | The http statuses on which retry is to be done. <br> **Default: [408, 413, 429, 500, 502, 503, 504, 521, 522, 524]** |
| `retry_methods` | `Array of string` | The http methods on which retry is to be done. <br> **Default: ['GET', 'PUT']** |
| `custom_header_authentication_credentials` | [`CustomHeaderAuthenticationCredentials`](doc/auth/custom-header-signature.md) | The credential object for Custom Header Signature |

The API client can be initialized as follows:

```python
client = PostnlecommerceClient(
    custom_header_authentication_credentials=CustomHeaderAuthenticationCredentials(
        apikey='apikey'
    )
)
```

API calls return an `ApiResponse` object that includes the following fields:

| Field | Description |
|  --- | --- |
| `status_code` | Status code of the HTTP response |
| `reason_phrase` | Reason phrase of the HTTP response |
| `headers` | Headers of the HTTP response as a dictionary |
| `text` | The body of the HTTP response as a string |
| `request` | HTTP request info |
| `errors` | Errors, if they exist |
| `body` | The deserialized body of the HTTP response |

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| Production server | **Default** Production server |
| Non-Production server | Sandbox environment for testing |

## Authorization

This API uses the following authentication schemes.

* [`APIKeyHeader (Custom Header Signature)`](doc/auth/custom-header-signature.md)

## List of APIs

* [Postalcodecheck](doc/controllers/postalcodecheck.md)
* [Barcode](doc/controllers/barcode.md)
* [Checkout](doc/controllers/checkout.md)
* [Confirming](doc/controllers/confirming.md)
* [Deliverydate](doc/controllers/deliverydate.md)
* [Labelling](doc/controllers/labelling.md)
* [Locations](doc/controllers/locations.md)
* [Shipment](doc/controllers/shipment.md)
* [Shipping Status](doc/controllers/shipping-status.md)
* [Timeframes](doc/controllers/timeframes.md)

## Classes Documentation

* [Utility Classes](doc/utility-classes.md)
* [HttpResponse](doc/http-response.md)
* [HttpRequest](doc/http-request.md)

