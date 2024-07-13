# XGA Builder API

<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

   * [Mock Builder REST API](#mock-builder-rest-api)
      + [Introduction](#introduction)
      + [Endpoints Summary](#endpoints-summary)
      + [Detailed Endpoint Documentation](#detailed-endpoint-documentation)
         - [Mock Error Endpoints](#mock-error-endpoints)
         - [Mock Built Payloads Endpoints](#mock-built-payloads-endpoints)
      + [Error Handling](#error-handling)
         - [Error Schema](#error-schema)
   * [Builder API v3.1](#builder-api-v31)
- [**getHeader**](#getheader)
      + [Parameters](#parameters)
   * [Return type](#return-type)
      + [GetHeaderResponse](#getheaderresponse)
         - [Properties](#properties)
      + [Authorization](#authorization)
      + [HTTP request headers](#http-request-headers)
- [**registerValidator**](#registervalidator)
      + [Parameters](#parameters-1)
      + [registerValidator_request_inner](#registervalidator_request_inner)
         - [Properties](#properties-1)
      + [Return type](#return-type-1)
      + [Authorization](#authorization-1)
      + [HTTP request headers](#http-request-headers-1)
- [**status**](#status)
      + [Parameters](#parameters-2)
      + [Return type](#return-type-2)
      + [Authorization](#authorization-2)
      + [HTTP request headers](#http-request-headers-2)
- [**submitBlindedBlock**](#submitblindedblock)
      + [Parameters](#parameters-3)
   * [Return type](#return-type-3)
      + [SubmitBlindedBlockResponse_data](#submitblindedblockresponse_data)
         - [Properties](#properties-2)
      + [Authorization](#authorization-3)
      + [HTTP request headers](#http-request-headers-3)

<!-- TOC end -->


<!-- TOC --><a name="mock-builder-rest-api"></a>
## Mock Builder REST API

<!-- TOC --><a name="introduction"></a>
### Introduction
This API allows Builders to enable and disable errors and modifications for various payloads. It provides endpoints to manage errors on payload requests and reveals, as well as to modify payload attributes and the payload itself.

<!-- TOC --><a name="endpoints-summary"></a>
### Endpoints Summary

| Method | Endpoint | Description |
|--------|----------|-------------|
| DELETE | `/mock/errors/payload_request` | Disables errors on `/eth/v1/builder/header/...` |
| POST | `/mock/errors/payload_request` | Enables errors on `/eth/v1/builder/header/...` |
| POST | `/mock/errors/payload_request/{slotOrEpoch}/{slotOrEpochNumber}` | Enables errors on `/eth/v1/builder/header/...` starting at the specified slot or epoch |
| DELETE | `/mock/errors/payload_reveal` | Disables errors on `/eth/v1/builder/blinded_blocks` |
| POST | `/mock/errors/payload_reveal` | Enables errors on `/eth/v1/builder/blinded_blocks` |
| POST | `/mock/errors/payload_reveal/{slotOrEpoch}/{slotOrEpochNumber}` | Enables errors on `/eth/v1/builder/blinded_blocks` starting at the specified slot or epoch |
| DELETE | `/mock/invalid/payload_attributes` | Disables any payload attributes modification |
| POST | `/mock/invalid/payload_attributes/{type}` | Enables specified type of payload attributes modification |
| POST | `/mock/invalid/payload_attributes/{type}/{slotOrEpoch}/{slotOrEpochNumber}` | Enables specified type of payload attributes modification starting at the specified slot or epoch |
| DELETE | `/mock/invalid/payload` | Disables any modification to payload built |
| POST | `/mock/invalid/payload/{type}` | Enables specified type of modification to payload built |
| POST | `/mock/invalid/payload/{type}/{slotOrEpoch}/{slotOrEpochNumber}` | Enables specified type of modification to payload built starting at the specified slot or epoch |

<!-- TOC --><a name="detailed-endpoint-documentation"></a>
### Detailed Endpoint Documentation

<!-- TOC --><a name="mock-error-endpoints"></a>
#### Mock Error Endpoints

- **DELETE** `/mock/errors/payload_request`
  - **Description**: Disables errors on `/eth/v1/builder/header/...`.
  - **Responses**:
    - `200`: Errors disabled successfully.

- **POST** `/mock/errors/payload_request`
  - **Description**: Enables errors on `/eth/v1/builder/header/...`.
  - **Responses**:
    - `200`: Errors enabled successfully.

- **POST** `/mock/errors/payload_request/{slotOrEpoch}/{slotOrEpochNumber}`
  - **Description**: Enables errors on `/eth/v1/builder/header/...` starting at the specified slot or epoch.
  - **Parameters**:
    - `slotOrEpoch` (path): Specify whether to use slot or epoch (enum: `slot`, `epoch`).
    - `slotOrEpochNumber` (path): The slot or epoch number to start enabling errors.
  - **Responses**:
    - `200`: Errors enabled successfully.

- **DELETE** `/mock/errors/payload_reveal`
  - **Description**: Disables errors on `/eth/v1/builder/blinded_blocks`.
  - **Responses**:
    - `200`: Errors disabled successfully.

- **POST** `/mock/errors/payload_reveal`
  - **Description**: Enables errors on `/eth/v1/builder/blinded_blocks`.
  - **Responses**:
    - `200`: Errors enabled successfully.

- **POST** `/mock/errors/payload_reveal/{slotOrEpoch}/{slotOrEpochNumber}`
  - **Description**: Enables errors on `/eth/v1/builder/blinded_blocks` starting at the specified slot or epoch.
  - **Parameters**:
    - `slotOrEpoch` (path): Specify whether to use slot or epoch (enum: `slot`, `epoch`).
    - `slotOrEpochNumber` (path): The slot or epoch number to start enabling errors.
  - **Responses**:
    - `200`: Errors enabled successfully.

<!-- TOC --><a name="mock-built-payloads-endpoints"></a>
#### Mock Built Payloads Endpoints

- **DELETE** `/mock/invalid/payload_attributes`
  - **Description**: Disables any payload attributes modification.
  - **Responses**:
    - `200`: Payload attributes modification disabled successfully.

- **POST** `/mock/invalid/payload_attributes/{type}`
  - **Description**: Enables specified type of payload attributes modification.
  - **Parameters**:
    - `type` (path): The type of payload attributes modification.
  - **Responses**:
    - `200`: Payload attributes modification enabled successfully.

- **POST** `/mock/invalid/payload_attributes/{type}/{slotOrEpoch}/{slotOrEpochNumber}`
  - **Description**: Enables specified type of payload attributes modification starting at the specified slot or epoch.
  - **Parameters**:
    - `type` (path): The type of payload attributes modification.
    - `slotOrEpoch` (path): Specify whether to use slot or epoch (enum: `slot`, `epoch`).
    - `slotOrEpochNumber` (path): The slot or epoch number to start enabling modification.
  - **Responses**:
    - `200`: Payload attributes modification enabled successfully.

- **DELETE** `/mock/invalid/payload`
  - **Description**: Disables any modification to payload built.
  - **Responses**:
    - `200`: Payload modification disabled successfully.

- **POST** `/mock/invalid/payload/{type}`
  - **Description**: Enables specified type of modification to payload built.
  - **Parameters**:
    - `type` (path): The type of payload modification.
  - **Responses**:
    - `200`: Payload modification enabled successfully.

- **POST** `/mock/invalid/payload/{type}/{slotOrEpoch}/{slotOrEpochNumber}`
  - **Description**: Enables specified type of modification to payload built starting at the specified slot or epoch.
  - **Parameters**:
    - `type` (path): The type of payload modification.
    - `slotOrEpoch` (path): Specify whether to use slot or epoch (enum: `slot`, `epoch`).
    - `slotOrEpochNumber` (path): The slot or epoch number to start enabling modification.
  - **Responses**:
    - `200`: Payload modification enabled successfully.

<!-- TOC --><a name="error-handling"></a>
### Error Handling
The API uses standard HTTP status codes to indicate the success or failure of a request. Additional error information is provided in the response body using the following schema:

<!-- TOC --><a name="error-schema"></a>
#### Error Schema

```yaml
components:
  schemas:
    Error:
      type: object
      properties:
        code:
          type: integer
        message:
          type: string
```

<!-- TOC --><a name="builder-api-v31"></a>
## Builder API v3.1


| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**getHeader**](BuilderApi.md#getHeader) | **GET** `/eth/v1/builder/header/{slot}/{parent_hash}/{pubkey}` | Get an execution payload header. |
| [**registerValidator**](BuilderApi.md#registerValidator) | **POST** `/eth/v1/builder/validators` | Register or update a validator&#39;s block building preferences. |
| [**status**](BuilderApi.md#status) | **GET** `/eth/v1/builder/status` | Check if builder is healthy. |
| [**submitBlindedBlock**](BuilderApi.md#submitBlindedBlock) | **POST** `/eth/v1/builder/blinded_blocks` | Submit a signed blinded block and get unblinded execution payload. |


<a name="getHeader"></a>
<!-- TOC --><a name="getheader"></a>
# **getHeader**
> GetHeaderResponse getHeader(slot, parent\_hash, pubkey)

Get an execution payload header.

    Requests a builder node to produce a valid execution payload header, which can be integrated into a blinded beacon block and signed.  If the builder is unable to produce a valid execution payload header, then the builder MUST return a 204 response. If the request is invalid, then the builder MUST return an error response (400) with a description of the validation failure.  After Deneb, return the KZG commitments for any associated blobs attached to the execution payload. 

<!-- TOC --><a name="parameters"></a>
### Parameters

|Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **slot** | **String**| The slot for which the block should be proposed. | [default to null] |
| **parent_hash** | **String**| Hash of execution layer block the proposer will build on. | [default to null] |
| **pubkey** | **String**| The validator&#39;s BLS public key. | [default to null] |

<!-- TOC --><a name="return-type"></a>
## Return type

<!-- TOC --><a name="getheaderresponse"></a>
### GetHeaderResponse
<!-- TOC --><a name="properties"></a>
#### Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **version** | **String** |  | [default to null] |
| **data** | [**GetHeaderResponse_data**](GetHeaderResponse_data.md) |  | [default to null] |

<!-- TOC --><a name="authorization"></a>
### Authorization

No authorization required

<!-- TOC --><a name="http-request-headers"></a>
### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

<a name="registerValidator"></a>
<!-- TOC --><a name="registervalidator"></a>
# **registerValidator**
> registerValidator(registerValidator_request_inner)

Register or update a validator&#39;s block building preferences.

    Registers a validator&#39;s preferred fee recipient and gas limit.  A success response (200) indicates that the registration was valid. If the registration passes validation, then the builder MUST integrate the registration into its state, such that future blocks built for the validator conform to the preferences expressed in the registration. If the registration is invalid, then the builder MUST return an error response (400) with a description of the validation failure. 

<!-- TOC --><a name="parameters-1"></a>
### Parameters

|Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **registerValidator_request_inner** | [**List**](#)| A signed declaration of a validator&#39;s block building preferences.  | |

<!-- TOC --><a name="registervalidator_request_inner"></a>
### registerValidator_request_inner
<!-- TOC --><a name="properties-1"></a>
#### Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **message** | [**registerValidator_request_inner_message**](#) |  | [default to null] |
| **signature** | **String** |  | [default to null] |

<!-- TOC --><a name="return-type-1"></a>
### Return type

null (empty response body)

<!-- TOC --><a name="authorization-1"></a>
### Authorization

No authorization required

<!-- TOC --><a name="http-request-headers-1"></a>
### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

<a name="status"></a>
<!-- TOC --><a name="status"></a>
# **status**
> status()

Check if builder is healthy.

    Checks if builder can respond to requests normally.

<!-- TOC --><a name="parameters-2"></a>
### Parameters
This endpoint does not need any parameter.

<!-- TOC --><a name="return-type-2"></a>
### Return type

null (empty response body)

<!-- TOC --><a name="authorization-2"></a>
### Authorization

No authorization required

<!-- TOC --><a name="http-request-headers-2"></a>
### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

<a name="submitBlindedBlock"></a>
<!-- TOC --><a name="submitblindedblock"></a>
# **submitBlindedBlock**
> SubmitBlindedBlockResponse submitBlindedBlock(submitBlindedBlock\_request, Eth-Consensus-Version)

Submit a signed blinded block and get unblinded execution payload.

    Submits a &#x60;SignedBlindedBeaconBlock&#x60; to the builder, binding the proposer to the block.  A success response (200) indicates that the signed blinded beacon block was valid. If the signed blinded beacon block was invalid, then the builder must return an error response (400) with a description of the validation failure.  After Deneb, this endpoint will additionally return the associated blobs in the response. 

<!-- TOC --><a name="parameters-3"></a>
### Parameters

|Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **submitBlindedBlock\_request** | [**submitBlindedBlock_request**](../Models/submitBlindedBlock_request.md)| A &#x60;SignedBlindedBeaconBlock&#x60;. | |
| **Eth-Consensus-Version** | **String**| Version of the block being submitted | [optional] [default to null] [enum: phase0, altair, bellatrix, capella, deneb, electra] |

<!-- TOC --><a name="return-type-3"></a>
## Return type

<!-- TOC --><a name="submitblindedblockresponse_data"></a>
### SubmitBlindedBlockResponse_data
<!-- TOC --><a name="properties-2"></a>
#### Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **parent_hash** | **String** |  | [default to null] |
| **fee_recipient** | **String** | An address on the execution (Ethereum 1) network. | [default to null] |
| **state_root** | **String** |  | [default to null] |
| **receipts_root** | **String** |  | [default to null] |
| **logs_bloom** | **String** |  | [default to null] |
| **prev_randao** | **String** |  | [default to null] |
| **block_number** | **String** |  | [default to null] |
| **gas_limit** | **String** |  | [default to null] |
| **gas_used** | **String** |  | [default to null] |
| **timestamp** | **String** |  | [default to null] |
| **extra_data** | **String** | Extra data on the execution (Ethereum 1) network. | [default to null] |
| **base_fee_per_gas** | **String** |  | [default to null] |
| **block_hash** | **String** |  | [default to null] |
| **transactions** | **List** |  | [default to null] |
| **withdrawals** | [**List**](#) |  | [default to null] |
| **execution_payload** | [**SubmitBlindedBlockResponse_data_oneOf_2_execution_payload**](#) |  | [default to null] |
| **blobs_bundle** | [**SubmitBlindedBlockResponse_data_oneOf_2_blobs_bundle**](#) |  | [default to null] |


<!-- TOC --><a name="authorization-3"></a>
### Authorization

No authorization required

<!-- TOC --><a name="http-request-headers-3"></a>
### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`


## Mock Builder REST API

### Introduction
This API allows Builders to enable and disable errors and modifications for various payloads. It provides endpoints to manage errors on payload requests and reveals, as well as to modify payload attributes and the payload itself.

### Endpoints Summary

| Method | Endpoint | Description |
|--------|----------|-------------|
| DELETE | `/mock/errors/payload_request` | Disables errors on `/eth/v1/builder/header/...` |
| POST | `/mock/errors/payload_request` | Enables errors on `/eth/v1/builder/header/...` |
| POST | `/mock/errors/payload_request/{slotOrEpoch}/{slotOrEpochNumber}` | Enables errors on `/eth/v1/builder/header/...` starting at the specified slot or epoch |
| DELETE | `/mock/errors/payload_reveal` | Disables errors on `/eth/v1/builder/blinded_blocks` |
| POST | `/mock/errors/payload_reveal` | Enables errors on `/eth/v1/builder/blinded_blocks` |
| POST | `/mock/errors/payload_reveal/{slotOrEpoch}/{slotOrEpochNumber}` | Enables errors on `/eth/v1/builder/blinded_blocks` starting at the specified slot or epoch |
| DELETE | `/mock/invalid/payload_attributes` | Disables any payload attributes modification |
| POST | `/mock/invalid/payload_attributes/{type}` | Enables specified type of payload attributes modification |
| POST | `/mock/invalid/payload_attributes/{type}/{slotOrEpoch}/{slotOrEpochNumber}` | Enables specified type of payload attributes modification starting at the specified slot or epoch |
| DELETE | `/mock/invalid/payload` | Disables any modification to payload built |
| POST | `/mock/invalid/payload/{type}` | Enables specified type of modification to payload built |
| POST | `/mock/invalid/payload/{type}/{slotOrEpoch}/{slotOrEpochNumber}` | Enables specified type of modification to payload built starting at the specified slot or epoch |

### Detailed Endpoint Documentation

#### Mock Error Endpoints

- **DELETE** `/mock/errors/payload_request`
  - **Description**: Disables errors on `/eth/v1/builder/header/...`.
  - **Responses**:
    - `200`: Errors disabled successfully.

- **POST** `/mock/errors/payload_request`
  - **Description**: Enables errors on `/eth/v1/builder/header/...`.
  - **Responses**:
    - `200`: Errors enabled successfully.

- **POST** `/mock/errors/payload_request/{slotOrEpoch}/{slotOrEpochNumber}`
  - **Description**: Enables errors on `/eth/v1/builder/header/...` starting at the specified slot or epoch.
  - **Parameters**:
    - `slotOrEpoch` (path): Specify whether to use slot or epoch (enum: `slot`, `epoch`).
    - `slotOrEpochNumber` (path): The slot or epoch number to start enabling errors.
  - **Responses**:
    - `200`: Errors enabled successfully.

- **DELETE** `/mock/errors/payload_reveal`
  - **Description**: Disables errors on `/eth/v1/builder/blinded_blocks`.
  - **Responses**:
    - `200`: Errors disabled successfully.

- **POST** `/mock/errors/payload_reveal`
  - **Description**: Enables errors on `/eth/v1/builder/blinded_blocks`.
  - **Responses**:
    - `200`: Errors enabled successfully.

- **POST** `/mock/errors/payload_reveal/{slotOrEpoch}/{slotOrEpochNumber}`
  - **Description**: Enables errors on `/eth/v1/builder/blinded_blocks` starting at the specified slot or epoch.
  - **Parameters**:
    - `slotOrEpoch` (path): Specify whether to use slot or epoch (enum: `slot`, `epoch`).
    - `slotOrEpochNumber` (path): The slot or epoch number to start enabling errors.
  - **Responses**:
    - `200`: Errors enabled successfully.

#### Mock Built Payloads Endpoints

- **DELETE** `/mock/invalid/payload_attributes`
  - **Description**: Disables any payload attributes modification.
  - **Responses**:
    - `200`: Payload attributes modification disabled successfully.

- **POST** `/mock/invalid/payload_attributes/{type}`
  - **Description**: Enables specified type of payload attributes modification.
  - **Parameters**:
    - `type` (path): The type of payload attributes modification.
  - **Responses**:
    - `200`: Payload attributes modification enabled successfully.

- **POST** `/mock/invalid/payload_attributes/{type}/{slotOrEpoch}/{slotOrEpochNumber}`
  - **Description**: Enables specified type of payload attributes modification starting at the specified slot or epoch.
  - **Parameters**:
    - `type` (path): The type of payload attributes modification.
    - `slotOrEpoch` (path): Specify whether to use slot or epoch (enum: `slot`, `epoch`).
    - `slotOrEpochNumber` (path): The slot or epoch number to start enabling modification.
  - **Responses**:
    - `200`: Payload attributes modification enabled successfully.

- **DELETE** `/mock/invalid/payload`
  - **Description**: Disables any modification to payload built.
  - **Responses**:
    - `200`: Payload modification disabled successfully.

- **POST** `/mock/invalid/payload/{type}`
  - **Description**: Enables specified type of modification to payload built.
  - **Parameters**:
    - `type` (path): The type of payload modification.
  - **Responses**:
    - `200`: Payload modification enabled successfully.

- **POST** `/mock/invalid/payload/{type}/{slotOrEpoch}/{slotOrEpochNumber}`
  - **Description**: Enables specified type of modification to payload built starting at the specified slot or epoch.
  - **Parameters**:
    - `type` (path): The type of payload modification.
    - `slotOrEpoch` (path): Specify whether to use slot or epoch (enum: `slot`, `epoch`).
    - `slotOrEpochNumber` (path): The slot or epoch number to start enabling modification.
  - **Responses**:
    - `200`: Payload modification enabled successfully.

### Error Handling
The API uses standard HTTP status codes to indicate the success or failure of a request. Additional error information is provided in the response body using the following schema:

#### Error Schema

```yaml
components:
  schemas:
    Error:
      type: object
      properties:
        code:
          type: integer
        message:
          type: string
```

## Builder API v3.1


| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**getHeader**](BuilderApi.md#getHeader) | **GET** `/eth/v1/builder/header/{slot}/{parent_hash}/{pubkey}` | Get an execution payload header. |
| [**registerValidator**](BuilderApi.md#registerValidator) | **POST** `/eth/v1/builder/validators` | Register or update a validator&#39;s block building preferences. |
| [**status**](BuilderApi.md#status) | **GET** `/eth/v1/builder/status` | Check if builder is healthy. |
| [**submitBlindedBlock**](BuilderApi.md#submitBlindedBlock) | **POST** `/eth/v1/builder/blinded_blocks` | Submit a signed blinded block and get unblinded execution payload. |


<a name="getHeader"></a>
# **getHeader**
> GetHeaderResponse getHeader(slot, parent\_hash, pubkey)

Get an execution payload header.

    Requests a builder node to produce a valid execution payload header, which can be integrated into a blinded beacon block and signed.  If the builder is unable to produce a valid execution payload header, then the builder MUST return a 204 response. If the request is invalid, then the builder MUST return an error response (400) with a description of the validation failure.  After Deneb, return the KZG commitments for any associated blobs attached to the execution payload. 

### Parameters

|Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **slot** | **String**| The slot for which the block should be proposed. | [default to null] |
| **parent_hash** | **String**| Hash of execution layer block the proposer will build on. | [default to null] |
| **pubkey** | **String**| The validator&#39;s BLS public key. | [default to null] |

## Return type

### GetHeaderResponse
#### Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **version** | **String** |  | [default to null] |
| **data** | [**GetHeaderResponse_data**](GetHeaderResponse_data.md) |  | [default to null] |

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: `application/json`

<a name="registerValidator"></a>
# **registerValidator**
> registerValidator(registerValidator_request_inner)

Register or update a validator&#39;s block building preferences.

    Registers a validator&#39;s preferred fee recipient and gas limit.  A success response (200) indicates that the registration was valid. If the registration passes validation, then the builder MUST integrate the registration into its state, such that future blocks built for the validator conform to the preferences expressed in the registration. If the registration is invalid, then the builder MUST return an error response (400) with a description of the validation failure. 

### Parameters

|Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **registerValidator_request_inner** | [**List**](#)| A signed declaration of a validator&#39;s block building preferences.  | |

### registerValidator_request_inner
#### Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **message** | [**registerValidator_request_inner_message**](#) |  | [default to null] |
| **signature** | **String** |  | [default to null] |

### Return type

null (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json

<a name="status"></a>
# **status**
> status()

Check if builder is healthy.

    Checks if builder can respond to requests normally.

### Parameters
This endpoint does not need any parameter.

### Return type

null (empty response body)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json

<a name="submitBlindedBlock"></a>
# **submitBlindedBlock**
> SubmitBlindedBlockResponse submitBlindedBlock(submitBlindedBlock\_request, Eth-Consensus-Version)

Submit a signed blinded block and get unblinded execution payload.

    Submits a &#x60;SignedBlindedBeaconBlock&#x60; to the builder, binding the proposer to the block.  A success response (200) indicates that the signed blinded beacon block was valid. If the signed blinded beacon block was invalid, then the builder must return an error response (400) with a description of the validation failure.  After Deneb, this endpoint will additionally return the associated blobs in the response. 

### Parameters

|Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **submitBlindedBlock\_request** | [**submitBlindedBlock_request**](../Models/submitBlindedBlock_request.md)| A &#x60;SignedBlindedBeaconBlock&#x60;. | |
| **Eth-Consensus-Version** | **String**| Version of the block being submitted | [optional] [default to null] [enum: phase0, altair, bellatrix, capella, deneb, electra] |

## Return type

### SubmitBlindedBlockResponse_data
#### Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
| **parent_hash** | **String** |  | [default to null] |
| **fee_recipient** | **String** | An address on the execution (Ethereum 1) network. | [default to null] |
| **state_root** | **String** |  | [default to null] |
| **receipts_root** | **String** |  | [default to null] |
| **logs_bloom** | **String** |  | [default to null] |
| **prev_randao** | **String** |  | [default to null] |
| **block_number** | **String** |  | [default to null] |
| **gas_limit** | **String** |  | [default to null] |
| **gas_used** | **String** |  | [default to null] |
| **timestamp** | **String** |  | [default to null] |
| **extra_data** | **String** | Extra data on the execution (Ethereum 1) network. | [default to null] |
| **base_fee_per_gas** | **String** |  | [default to null] |
| **block_hash** | **String** |  | [default to null] |
| **transactions** | **List** |  | [default to null] |
| **withdrawals** | [**List**](#) |  | [default to null] |
| **execution_payload** | [**SubmitBlindedBlockResponse_data_oneOf_2_execution_payload**](#) |  | [default to null] |
| **blobs_bundle** | [**SubmitBlindedBlockResponse_data_oneOf_2_blobs_bundle**](#) |  | [default to null] |


### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: `application/json`
- **Accept**: `application/json`

