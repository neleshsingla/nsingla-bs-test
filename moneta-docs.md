# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [AffinityService.proto](#AffinityService-proto)
    - [AffinityDetailsByAffinitiesBitmapRequest](#com-brandwatch-moneta-rpc-affinityservice-AffinityDetailsByAffinitiesBitmapRequest)
    - [AffinityOrdinalRequest](#com-brandwatch-moneta-rpc-affinityservice-AffinityOrdinalRequest)
    - [AffinityOrdinalResponse](#com-brandwatch-moneta-rpc-affinityservice-AffinityOrdinalResponse)
    - [AffinityTypeDetailsByNameRequest](#com-brandwatch-moneta-rpc-affinityservice-AffinityTypeDetailsByNameRequest)
    - [CreateAffinityRequest](#com-brandwatch-moneta-rpc-affinityservice-CreateAffinityRequest)
    - [CreateAffinityResponse](#com-brandwatch-moneta-rpc-affinityservice-CreateAffinityResponse)
    - [CreateAffinityTypeRequest](#com-brandwatch-moneta-rpc-affinityservice-CreateAffinityTypeRequest)
    - [CreateAffinityTypeResponse](#com-brandwatch-moneta-rpc-affinityservice-CreateAffinityTypeResponse)
    - [DeleteAffinityByOrdinalRequest](#com-brandwatch-moneta-rpc-affinityservice-DeleteAffinityByOrdinalRequest)
    - [DeleteAffinityByOrdinalResponse](#com-brandwatch-moneta-rpc-affinityservice-DeleteAffinityByOrdinalResponse)
    - [FindAffinityByDisplayNameAndTypeRequest](#com-brandwatch-moneta-rpc-affinityservice-FindAffinityByDisplayNameAndTypeRequest)
    - [FindAffinityByDisplayNameAndTypeResponse](#com-brandwatch-moneta-rpc-affinityservice-FindAffinityByDisplayNameAndTypeResponse)
    - [ReadAffinityByOrdinalRequest](#com-brandwatch-moneta-rpc-affinityservice-ReadAffinityByOrdinalRequest)
    - [ReadAffinityByOrdinalResponse](#com-brandwatch-moneta-rpc-affinityservice-ReadAffinityByOrdinalResponse)
    - [TopAffinitiesForSiteAuthorsRequest](#com-brandwatch-moneta-rpc-affinityservice-TopAffinitiesForSiteAuthorsRequest)
    - [TopOrdinalCount](#com-brandwatch-moneta-rpc-affinityservice-TopOrdinalCount)
    - [UpdateAffinityByOrdinalRequest](#com-brandwatch-moneta-rpc-affinityservice-UpdateAffinityByOrdinalRequest)
    - [UpdateAffinityByOrdinalResponse](#com-brandwatch-moneta-rpc-affinityservice-UpdateAffinityByOrdinalResponse)
  
    - [AffinityService](#com-brandwatch-moneta-rpc-affinityservice-AffinityService)
  
- [BioTopXService.proto](#BioTopXService-proto)
    - [TopBioTokenCountRequest](#com-brandwatch-moneta-rpc-biotopxservice-TopBioTokenCountRequest)
    - [TopTokenCount](#com-brandwatch-moneta-rpc-biotopxservice-TopTokenCount)
  
    - [BioType](#com-brandwatch-moneta-rpc-biotopxservice-BioType)
  
    - [BioTopXService](#com-brandwatch-moneta-rpc-biotopxservice-BioTopXService)
  
- [ProfileServices.proto](#ProfileServices-proto)
    - [RedditChannelProfileService](#com-brandwatch-moneta-rpc-profileservices-RedditChannelProfileService)
    - [RedditUserProfileService](#com-brandwatch-moneta-rpc-profileservices-RedditUserProfileService)
    - [TwitterUserProfileService](#com-brandwatch-moneta-rpc-profileservices-TwitterUserProfileService)
  
- [Scalar Value Types](#scalar-value-types)



<a name="AffinityService-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## AffinityService.proto



<a name="com-brandwatch-moneta-rpc-affinityservice-AffinityDetailsByAffinitiesBitmapRequest"></a>

### AffinityDetailsByAffinitiesBitmapRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| affinitiesRoaringBitmap | [bytes](#bytes) |  | 32 bit roaring bitmap serialized to a byte buffer. |






<a name="com-brandwatch-moneta-rpc-affinityservice-AffinityOrdinalRequest"></a>

### AffinityOrdinalRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| displayName | [string](#string) |  |  |
| type | [string](#string) |  |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-AffinityOrdinalResponse"></a>

### AffinityOrdinalResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ordinal | [fixed32](#fixed32) |  |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-AffinityTypeDetailsByNameRequest"></a>

### AffinityTypeDetailsByNameRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| typeNames | [string](#string) | repeated |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-CreateAffinityRequest"></a>

### CreateAffinityRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| displayName | [string](#string) |  | can be used for display purposes. |
| type | [string](#string) |  | affinity type. |
| hidden | [bool](#bool) | optional | if true, this affinity will never be returned from getAffinityDetailsByAffinitiesBitmap. |
| authorsRoaringBitmap | [bytes](#bytes) |  | 32 bit roaring bitmap serialized to a byte buffer, referring to the authors for the given affinity type&#39;s site. |
| ordinal | [fixed32](#fixed32) | optional | currently required and will throw an error if left out. In the future, will generate a new ordinal on demand. |






<a name="com-brandwatch-moneta-rpc-affinityservice-CreateAffinityResponse"></a>

### CreateAffinityResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ordinal | [fixed32](#fixed32) |  |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-CreateAffinityTypeRequest"></a>

### CreateAffinityTypeRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | unique type name. Can NOT be used for display purposes. |
| site | [string](#string) |  | site, e.g. twitter.com, reddit.com |
| hidden | [bool](#bool) |  | if true, this affinity type and all associated affinities will never be returned from getAffinityDetailsByAffinitiesBitmap or getAffinityTypeDetailsByName. |






<a name="com-brandwatch-moneta-rpc-affinityservice-CreateAffinityTypeResponse"></a>

### CreateAffinityTypeResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| name | [string](#string) |  | unique type name. Can NOT be used for display purposes. |
| site | [string](#string) |  | site, e.g. twitter.com, reddit.com |






<a name="com-brandwatch-moneta-rpc-affinityservice-DeleteAffinityByOrdinalRequest"></a>

### DeleteAffinityByOrdinalRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ordinal | [fixed32](#fixed32) |  |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-DeleteAffinityByOrdinalResponse"></a>

### DeleteAffinityByOrdinalResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ordinal | [fixed32](#fixed32) |  |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-FindAffinityByDisplayNameAndTypeRequest"></a>

### FindAffinityByDisplayNameAndTypeRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| displayName | [string](#string) |  | can be used for display purposes. |
| type | [string](#string) |  | affinity type. |






<a name="com-brandwatch-moneta-rpc-affinityservice-FindAffinityByDisplayNameAndTypeResponse"></a>

### FindAffinityByDisplayNameAndTypeResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| displayName | [string](#string) |  | can be used for display purposes. |
| type | [string](#string) |  | affinity type. |
| hidden | [bool](#bool) |  | if true, this affinity will never be returned from getAffinityDetailsByAffinitiesBitmap. |
| authorsRoaringBitmap | [bytes](#bytes) |  | 32 bit roaring bitmap serialized to a byte buffer, referring to the authors for the given affinity type&#39;s site. |
| ordinal | [fixed32](#fixed32) |  |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-ReadAffinityByOrdinalRequest"></a>

### ReadAffinityByOrdinalRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ordinal | [fixed32](#fixed32) |  |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-ReadAffinityByOrdinalResponse"></a>

### ReadAffinityByOrdinalResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| displayName | [string](#string) |  | can be used for display purposes. |
| type | [string](#string) |  | affinity type. |
| hidden | [bool](#bool) |  | if true, this affinity will never be returned from getAffinityDetailsByAffinitiesBitmap. |
| authorsRoaringBitmap | [bytes](#bytes) |  | 32 bit roaring bitmap serialized to a byte buffer, referring to the authors for the given affinity type&#39;s site. |
| ordinal | [fixed32](#fixed32) |  |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-TopAffinitiesForSiteAuthorsRequest"></a>

### TopAffinitiesForSiteAuthorsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| siteAuthors | [com.brandwatch.moneta.rpc.dto.SiteAuthorsDTO](#com-brandwatch-moneta-rpc-dto-SiteAuthorsDTO) | repeated |  |
| limit | [int64](#int64) |  | default is zero and will return nothing. negative will throw an error. |






<a name="com-brandwatch-moneta-rpc-affinityservice-TopOrdinalCount"></a>

### TopOrdinalCount



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ordinal | [fixed32](#fixed32) |  |  |
| count | [int64](#int64) |  |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-UpdateAffinityByOrdinalRequest"></a>

### UpdateAffinityByOrdinalRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| displayName | [string](#string) | optional | can be used for display purposes. |
| type | [string](#string) | optional | affinity type. |
| hidden | [bool](#bool) | optional | if true, this affinity will never be returned from getAffinityDetailsByAffinitiesBitmap. |
| authorsRoaringBitmap | [bytes](#bytes) | optional | 32 bit roaring bitmap serialized to a byte buffer, referring to the authors for the given affinity type&#39;s site. |
| ordinal | [fixed32](#fixed32) |  |  |






<a name="com-brandwatch-moneta-rpc-affinityservice-UpdateAffinityByOrdinalResponse"></a>

### UpdateAffinityByOrdinalResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ordinal | [fixed32](#fixed32) |  |  |





 

 

 


<a name="com-brandwatch-moneta-rpc-affinityservice-AffinityService"></a>

### AffinityService


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| createAffinity | [CreateAffinityRequest](#com-brandwatch-moneta-rpc-affinityservice-CreateAffinityRequest) | [CreateAffinityResponse](#com-brandwatch-moneta-rpc-affinityservice-CreateAffinityResponse) | create an affinity with the specified data |
| deleteAffinityByOrdinal | [DeleteAffinityByOrdinalRequest](#com-brandwatch-moneta-rpc-affinityservice-DeleteAffinityByOrdinalRequest) | [DeleteAffinityByOrdinalResponse](#com-brandwatch-moneta-rpc-affinityservice-DeleteAffinityByOrdinalResponse) | delete an affinity with a specified ordinal |
| readAffinityByOrdinal | [ReadAffinityByOrdinalRequest](#com-brandwatch-moneta-rpc-affinityservice-ReadAffinityByOrdinalRequest) | [ReadAffinityByOrdinalResponse](#com-brandwatch-moneta-rpc-affinityservice-ReadAffinityByOrdinalResponse) | read affinity details of a specified ordinal |
| findAffinityByDisplayNameAndType | [FindAffinityByDisplayNameAndTypeRequest](#com-brandwatch-moneta-rpc-affinityservice-FindAffinityByDisplayNameAndTypeRequest) | [FindAffinityByDisplayNameAndTypeResponse](#com-brandwatch-moneta-rpc-affinityservice-FindAffinityByDisplayNameAndTypeResponse) | find affinity with a specified display name and type combination |
| updateAffinityByOrdinal | [UpdateAffinityByOrdinalRequest](#com-brandwatch-moneta-rpc-affinityservice-UpdateAffinityByOrdinalRequest) | [UpdateAffinityByOrdinalResponse](#com-brandwatch-moneta-rpc-affinityservice-UpdateAffinityByOrdinalResponse) | update specified fields of an affinity given an ordinal |
| topAffinitiesForSiteAuthors | [TopAffinitiesForSiteAuthorsRequest](#com-brandwatch-moneta-rpc-affinityservice-TopAffinitiesForSiteAuthorsRequest) | [TopOrdinalCount](#com-brandwatch-moneta-rpc-affinityservice-TopOrdinalCount) stream | request the top affinities for one or more sets of authors, by site |
| getAffinityDetailsByAffinitiesBitmap | [AffinityDetailsByAffinitiesBitmapRequest](#com-brandwatch-moneta-rpc-affinityservice-AffinityDetailsByAffinitiesBitmapRequest) | [.com.brandwatch.moneta.rpc.dto.AffinityDTO](#com-brandwatch-moneta-rpc-dto-AffinityDTO) stream | get affinity details, including display name and type, for a set of affinities. Will not return hidden affinities or affinities of hidden types. |
| getAffinityTypeDetailsByName | [AffinityTypeDetailsByNameRequest](#com-brandwatch-moneta-rpc-affinityservice-AffinityTypeDetailsByNameRequest) | [.com.brandwatch.moneta.rpc.dto.AffinityTypeDTO](#com-brandwatch-moneta-rpc-dto-AffinityTypeDTO) stream | get affinity type details. Will not return hidden types. |
| createAffinityType | [CreateAffinityTypeRequest](#com-brandwatch-moneta-rpc-affinityservice-CreateAffinityTypeRequest) | [CreateAffinityTypeResponse](#com-brandwatch-moneta-rpc-affinityservice-CreateAffinityTypeResponse) | create an affinity type, with a corresponding site. |
| getAffinityOrdinal | [AffinityOrdinalRequest](#com-brandwatch-moneta-rpc-affinityservice-AffinityOrdinalRequest) | [AffinityOrdinalResponse](#com-brandwatch-moneta-rpc-affinityservice-AffinityOrdinalResponse) | search for an affinity ordinal by display name and type. Will not return hidden affinities or affinities of hidden types. |
| getAllAuthorsWithAffinities | [.com.brandwatch.moneta.rpc.dto.Empty](#com-brandwatch-moneta-rpc-dto-Empty) | [.com.brandwatch.moneta.rpc.dto.SiteAuthorsDTO](#com-brandwatch-moneta-rpc-dto-SiteAuthorsDTO) stream | get all authors with any affinity |

 



<a name="BioTopXService-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## BioTopXService.proto



<a name="com-brandwatch-moneta-rpc-biotopxservice-TopBioTokenCountRequest"></a>

### TopBioTokenCountRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| bioType | [BioType](#com-brandwatch-moneta-rpc-biotopxservice-BioType) |  | one of the bio types we currently support. |
| authorsRoaringBitmap | [bytes](#bytes) |  | 32 bit roaring bitmap serialized to a byte buffer, referring to the authors for the given bio type&#39;s site. |
| limit | [int64](#int64) |  | default is zero and will return nothing. negative will throw an error. |






<a name="com-brandwatch-moneta-rpc-biotopxservice-TopTokenCount"></a>

### TopTokenCount



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| token | [string](#string) |  | token for display purposes. |
| count | [int64](#int64) |  |  |





 


<a name="com-brandwatch-moneta-rpc-biotopxservice-BioType"></a>

### BioType


| Name | Number | Description |
| ---- | ------ | ----------- |
| TWITTER_AUTHOR_BIO | 0 |  |


 

 


<a name="com-brandwatch-moneta-rpc-biotopxservice-BioTopXService"></a>

### BioTopXService


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| topBioTokenCount | [TopBioTokenCountRequest](#com-brandwatch-moneta-rpc-biotopxservice-TopBioTokenCountRequest) | [TopTokenCount](#com-brandwatch-moneta-rpc-biotopxservice-TopTokenCount) stream | get the top bio tokens, in descending count, for a given bio type |

 



<a name="ProfileServices-proto"></a>
<p align="right"><a href="#top">Top</a></p>

## ProfileServices.proto


 

 

 


<a name="com-brandwatch-moneta-rpc-profileservices-RedditChannelProfileService"></a>

### RedditChannelProfileService


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| findOrdinalsForIds | [.com.brandwatch.moneta.rpc.dto.StringId](#com-brandwatch-moneta-rpc-dto-StringId) stream | [.com.brandwatch.moneta.rpc.dto.OrdinalStringId](#com-brandwatch-moneta-rpc-dto-OrdinalStringId) stream | Lookup ordinals for a given set of Reddit channel IDs |
| findOrdinalsForChannelNames | [.com.brandwatch.moneta.rpc.dto.Name](#com-brandwatch-moneta-rpc-dto-Name) stream | [.com.brandwatch.moneta.rpc.dto.OrdinalName](#com-brandwatch-moneta-rpc-dto-OrdinalName) stream | Lookup ordinals for a given set of Reddit channel names |
| getProfiles | [.com.brandwatch.moneta.rpc.dto.Ordinal](#com-brandwatch-moneta-rpc-dto-Ordinal) stream | [.com.brandwatch.moneta.rpc.dto.RedditChannelProfile](#com-brandwatch-moneta-rpc-dto-RedditChannelProfile) stream | Get Reddit channel profile by ordinal |


<a name="com-brandwatch-moneta-rpc-profileservices-RedditUserProfileService"></a>

### RedditUserProfileService


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| findOrdinalsForIds | [.com.brandwatch.moneta.rpc.dto.StringId](#com-brandwatch-moneta-rpc-dto-StringId) stream | [.com.brandwatch.moneta.rpc.dto.OrdinalStringId](#com-brandwatch-moneta-rpc-dto-OrdinalStringId) stream | Lookup ordinals for a given set of Reddit user IDs |
| findOrdinalsForUsernames | [.com.brandwatch.moneta.rpc.dto.Name](#com-brandwatch-moneta-rpc-dto-Name) stream | [.com.brandwatch.moneta.rpc.dto.OrdinalName](#com-brandwatch-moneta-rpc-dto-OrdinalName) stream | Lookup ordinals for a given set of Reddit user names |
| getProfiles | [.com.brandwatch.moneta.rpc.dto.Ordinal](#com-brandwatch-moneta-rpc-dto-Ordinal) stream | [.com.brandwatch.moneta.rpc.dto.RedditUserProfile](#com-brandwatch-moneta-rpc-dto-RedditUserProfile) stream | Get Reddit user profile by ordinal |


<a name="com-brandwatch-moneta-rpc-profileservices-TwitterUserProfileService"></a>

### TwitterUserProfileService


| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| findOrdinalsForIds | [.com.brandwatch.moneta.rpc.dto.LongId](#com-brandwatch-moneta-rpc-dto-LongId) stream | [.com.brandwatch.moneta.rpc.dto.OrdinalLongId](#com-brandwatch-moneta-rpc-dto-OrdinalLongId) stream | Lookup ordinals for a given set of Twitter user IDs |
| findOrdinalsForUsernames | [.com.brandwatch.moneta.rpc.dto.Name](#com-brandwatch-moneta-rpc-dto-Name) stream | [.com.brandwatch.moneta.rpc.dto.OrdinalName](#com-brandwatch-moneta-rpc-dto-OrdinalName) stream | Lookup ordinals for a given set of Twitter user names |
| getProfiles | [.com.brandwatch.moneta.rpc.dto.Ordinal](#com-brandwatch-moneta-rpc-dto-Ordinal) stream | [.com.brandwatch.moneta.rpc.dto.TwitterUserProfile](#com-brandwatch-moneta-rpc-dto-TwitterUserProfile) stream | Get Twitter user profile by ordinal |

 



## Scalar Value Types

| .proto Type | Notes | C++ | Java | Python | Go | C# | PHP | Ruby |
| ----------- | ----- | --- | ---- | ------ | -- | -- | --- | ---- |
| <a name="double" /> double |  | double | double | float | float64 | double | float | Float |
| <a name="float" /> float |  | float | float | float | float32 | float | float | Float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum or Fixnum (as required) |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="bool" /> bool |  | bool | boolean | boolean | bool | bool | boolean | TrueClass/FalseClass |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode | string | string | string | String (UTF-8) |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str | []byte | ByteString | string | String (ASCII-8BIT) |
