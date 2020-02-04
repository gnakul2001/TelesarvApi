# TeleSarv API

TeleSarv API is build for TeleSarv - Bulk SMS Application For Marketing


### Prerequisites

To run TeleSarv API you have to install TeleSarv Application on your server. 
For more details please visit: [TeleSarv](https://telesarv.com/)
```
php >=5.6
TeleSarv - Bulk SMS Application For Markting
```

### Installing
Via Composer
```
composer require gnakul2001/telesarv-api
```

And Via Bash

```
git clone https://github.com/gnakul2001/TelesarvApi.git
```

## Usage


 ### Step 1:
If install TeleSarv API using Git Clone then load your TeleSarv API Class file and Use namespace. 
```php
require_once 'src/Class_TeleSarv_API.php';
use TeleSarv\TelesarvApi;
```
If install TeleSarv API using Composer then Require/Include autoload.php file in the index.php of your project or whatever file you need to use **TeleSarv API** classes:. 
```php
require 'vendor/autoload.php';
use TeleSarv\TelesarvApi;
```
### Step 2:
set your API_KEY from `https://mywebhost.com/sms-api/info` (your application install url)
```php
$api_key = 'YWRtaW46YWRtaW4ucGFzc3dvcmQ=';
```
### Step 3:
Change the from number below. It can be a valid phone number or a String
```php
$from = '8801721000000';
```

### Step 4:
the number we are sending to - Any phone number
```php
$destination = '8801810000000';
```
For multiple number please use Comma (,) after every single number.
```php
$destination = '8801810000000,8801721000000,880167000000,01913000000';
```
You can insert maximum 100 numbers using comma in single api request.

You have to must include Country code at beginning of the phone number.  

### Step 5:
Replace your Install URL like `https://mywebhost.com/sms/api` with `https://demo.telesarvpanel.com/`
`sms/api` is mandatory on your install url

```php
$url = 'https://demo.telesarvpanel.com/sms/api';
```
// SMS Body
```php
$sms = 'test message from TeleSarv';
```
// Unicode SMS
```php
$unicode = '1'; //For Unicode message
```
// MMS SMS
```php
$mms = '1'; //For mms message
$media_url = 'https://yourmediaurl.com'; //Insert your media url
```
// Schedule SMS
```php
$schedule_date = '07/07/2017 12:20 PM'; //Date like this format: m/d/Y h:i A
```
// Message Type
```php
$type = 'TRANS'; //TRANS OR PROMO
```
// Create Plain/text SMS Body for request
```php
$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms,
    'type' => $type
);
```
// Create Unicode SMS Body for request
```php
$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms,
    'unicode' => $unicode,
    'type' => $type
);
```
// Create MMS SMS Body for request
```php
$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms, //optional
    'mms' => $mms,
    'media_url' => $media_url,
    'type' => $type
);
```
// Create Schedule SMS Body for request
```php
$sms_body = array(
    'api_key' => $api_key,
    'to' => $destination,
    'from' => $from,
    'sms' => $sms,
    'schedule' => $schedule_date,
    'type' => $type
);
```

### Step 6: 
Instantiate a new TeleSarv API request
```php
$client = new TelesarvApi();
```

## Send SMS
Finally send your sms through TeleSarv API
```php
$response = $client->send_sms($sms_body, $url);
```

## Get Inbox
Get your all message
```php
$get_inbox=$client->get_inbox($api_key,$url);
```

## Get Balance
Get your account balance
```php
$get_balance=$client->check_balance($api_key,$url);
```
## Response
TeleSarv API return response with `json` format, like:

```json
{"code":"ok","message":"Successfully Send"}
```

## Status Code

| Status | Message |
| --- | --- |
| `ok` | Successfully Send |
| `100` | Bad gateway requested |
| `101` | Wrong action |
| `102` | Authentication failed |
| `103` | Invalid phone number |
| `104` | Phone coverage not active |
| `105` | Insufficient balance |
| `106` | Invalid Sender ID |
| `107` | Invalid SMS Type |
| `108` | SMS Gateway not active |
| `109` | Invalid Schedule Time |
| `110` | Media url required |
| `111` | SMS contain spam word. Wait for approval |

## Authors

* **Nakul Gupta** - *Initial work* - [gnakul2001](https://github.com/gnakul2001)
