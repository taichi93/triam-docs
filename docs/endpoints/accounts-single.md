---
Account Details
---
Returns information and links relating to a single [account](../resources/account.md).

The balances section in the returned JSON will also list all the [trust lines](https://www.triamnetwork.com/developers/learn/concepts/assets.html) this account has set up. Note this will only return trustlines that have the necessary authorization to work. Meaning if an accountA trusts another accountB that has the [authorization required](https://www.triamnetwork.com/developers/guides/concepts/accounts.html#flags) flag set the trustline wont show up until accountB [allows](https://www.triamnetwork.com/developers/guides/concepts/list-of-operations.html#allow-trust) accountA to hold its assets.

## Request

```
GET /accounts/{account}
```

### Arguments

| name | notes | description | example |
| ---- | ----- | ----------- | ------- |
| `account` | required, string | Account ID | GA2HGBJIJKI6O4XEM7CZWY5PS6GKSXL6D34ERAJYQSPYA6X6AI7HYW36 |

## Response

This endpoint responds with the details of a single account for a given ID. See [account resource](../resources/account.md) for reference.

### Example Request
::: tabs language

- curl
  ```curl
  curl "https://testnet-horizon.triamnetwork.com/accounts/GCEZWKCA5VLDNRLN3RPRJMRZOX3Z6G5CHCGSNFHEYVXM3XOJMDS674JZ"
  ```
- JavaScript
  ```js
  var TriamSdk = require('triam-sdk');
  var server = new TriamSdk.Server('https://testnet-horizon.triamnetwork.com/');

  server.accounts()
    .accountId("GCEZWKCA5VLDNRLN3RPRJMRZOX3Z6G5CHCGSNFHEYVXM3XOJMDS674JZ")
    .call()
    .then(function (accountResult) {
      console.log(accountResult);
    })
    .catch(function (err) {
      console.error(err);
    })
  ```
- Try it out
  https://laboratory.triamnetwork.com/#explorer?resource=accounts&endpoint=single

:::
### Example Response
```json
{
  "_links": {
    "self": {
      "href": "https://testnet-horizon.triamnetwork.com/accounts/GD42RQNXTRIW6YR3E2HXV5T2AI27LBRHOERV2JIYNFMXOBA234SWLQQB"
    },
    "transactions": {
      "href": "https://testnet-horizon.triamnetwork.com/accounts/GD42RQNXTRIW6YR3E2HXV5T2AI27LBRHOERV2JIYNFMXOBA234SWLQQB/transactions{?cursor,limit,order}",
      "templated": true
    },
    "operations": {
      "href": "https://testnet-horizon.triamnetwork.com/accounts/GD42RQNXTRIW6YR3E2HXV5T2AI27LBRHOERV2JIYNFMXOBA234SWLQQB/operations{?cursor,limit,order}",
      "templated": true
    },
    "payments": {
      "href": "https://testnet-horizon.triamnetwork.com/accounts/GD42RQNXTRIW6YR3E2HXV5T2AI27LBRHOERV2JIYNFMXOBA234SWLQQB/payments{?cursor,limit,order}",
      "templated": true
    },
    "effects": {
      "href": "https://testnet-horizon.triamnetwork.com/accounts/GD42RQNXTRIW6YR3E2HXV5T2AI27LBRHOERV2JIYNFMXOBA234SWLQQB/effects{?cursor,limit,order}",
      "templated": true
    },
    "offers": {
      "href": "https://testnet-horizon.triamnetwork.com/accounts/GD42RQNXTRIW6YR3E2HXV5T2AI27LBRHOERV2JIYNFMXOBA234SWLQQB/offers{?cursor,limit,order}",
      "templated": true
    }
  },
  "id": "GD42RQNXTRIW6YR3E2HXV5T2AI27LBRHOERV2JIYNFMXOBA234SWLQQB",
  "paging_token": "7275146318450689",
  "account_id": "GD42RQNXTRIW6YR3E2HXV5T2AI27LBRHOERV2JIYNFMXOBA234SWLQQB",
  "sequence": 7275146318446606,
  "subentry_count": 5,
  "thresholds": {
    "low_threshold": 0,
    "med_threshold": 0,
    "high_threshold": 0
  },
  "flags": {
    "auth_required": false,
    "auth_revocable": false
  },
  "balances": [
    {
      "balance": "126.8107491",
      "limit": "5000.0000000",
      "asset_type": "credit_alphanum4",
      "asset_code": "BAR",
      "asset_issuer": "GBAUUA74H4XOQYRSOW2RZUA4QL5PB37U3JS5NE3RTB2ELJVMIF5RLMAG"
    },
    {
      "balance": "294.0000000",
      "limit": "922337203685.4775807",
      "asset_type": "credit_alphanum4",
      "asset_code": "FOO",
      "asset_issuer": "GBAUUA74H4XOQYRSOW2RZUA4QL5PB37U3JS5NE3RTB2ELJVMIF5RLMAG"
    },
    {
      "balance": "9997.6802725",
      "asset_type": "native"
    }
  ],
  "signers": [
    {
      "public_key": "GD42RQNXTRIW6YR3E2HXV5T2AI27LBRHOERV2JIYNFMXOBA234SWLQQB",
      "weight": 1
    }
  ],
  "data": {
    "club": "MTAw"
  }
}
```
