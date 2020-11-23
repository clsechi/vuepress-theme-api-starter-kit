<Block>

# Exchanges

</Block>

<Block>

## Quotations

### Endpoint

```text
GET /v1/exchanges/paper-money/quotations/:merchant_id?currency=USD&value=23500&reverse=false
```

This route is responsible for the return of quotation information about all currencies.

It is possible to inform the quotation of a specific currency and value should all query params are passed.

If the quotation exceeds the minimum or the maximum limit, the offer will rounded for the limits range and a rounding attribute will be returned with information about it.

- NORMAL: The value is in the limits range
- MINIMUM: The value is lower than minimum to sell
- MAXIMUM: The value is higher than maximum to sell

The value passed in the URL parameter must be multiplied by 100, as it has precision of two decimal places, for example, for a quote of 100, it would send 10000. For structures with value and divisor, value refers to the entire value, and the divisor refers to the precision of that value. To obtain the result with decimal places, just divide the value by the divisor.

For more information check the examples request.

### Parameters

| Name | Example | Description | Required |
|-|-|-|-|
| currency | USD | Currency to generate quotation for | :heavy_check_mark: |
| value | 26500 | Value proposal to generate | :heavy_check_mark: |
| reverse | false | If generation should be reversed, that is, if TRUE will generate quotation from BRL to given currency | :heavy_check_mark: |

::: tip
This is a tip
:::

::: warning
This is a warning
:::

::: danger
This is a dangerous warning
:::

::: details
This route is responsible for the return of quotation information about all currencies.

It is possible to inform the quotation of a specific currency and value should all query params are passed.

If the quotation exceeds the minimum or the maximum limit, the offer will rounded for the limits range and a rounding attribute will be returned with information about it.

- NORMAL: The value is in the limits range
- MINIMUM: The value is lower than minimum to sell
- MAXIMUM: The value is higher than maximum to sell

The value passed in the URL parameter must be multiplied by 100, as it has precision of two decimal places, for example, for a quote of 100, it would send 10000. For structures with value and divisor, value refers to the entire value, and the divisor refers to the precision of that value. To obtain the result with decimal places, just divide the value by the divisor.

For more information check the examples request.
:::

### Response

```json
Status: 200 OK

{
  "id": "9aa26c09265a73aa7b30e7173b6f8358a099450f",
  "reverse": true,
  "purposeCode": "IR003",
  "currency": {
    "countryFlagUrl": "https://s3.amazonaws.com/frente-exchanges/flags/united-states.svg",
    "code": "USD",
    "name": "Dólar Americano",
    "coverageRatePercentage": 89,
    "offer": 184,
    "offerUSD": {
      "value": 1840000,
      "divisor": 10000
    },
    "parityFromUSD": {
      "value": 10000,
      "divisor": 10000
    },
    "parityToUSD": {
      "value": 10000,
      "divisor": 10000
    },
    "spreadPercentage": 2.52,
    "maxToSell": 65320,
    "minToSell": 184,
    "multiples": [
      20,
      50,
      100
    ],
    "commercialExchangeRate": {
      "value": 38360,
      "divisor": 10000
    },
    "levelingRate": {
      "value": 72500,
      "divisor": 10000
    }
  },
  "tax": {
    "iof": {
      "percentage": 1.1,
      "total": {
        "value": 1504,
        "divisor": 100
      }
    }
  },
  "price": {
    "withoutTax": {
      "value": 74327,
      "divisor": 10000
    },
    "withTax": {
      "value": 75145,
      "divisor": 10000
    }
  },
  "total": {
    "withoutTax": {
      "value": 136762,
      "divisor": 100
    },
    "withTax": {
      "value": 138267,
      "divisor": 100
    }
  },
  "createdAt": "2019-11-06T14:18:57.572Z",
  "expiresAt": "2019-11-06T14:28:57.000Z",
  "timeToLive": 600,
  "merchantId": "WL-FRENTE-SP",
  "rounding": {
    "method": "MINIMUM",
    "rounded": true
  }
}
```

### Error

```json
Status: 400 BAD REQUEST

{
  "error": "Invalid parameters"
}
```

<Example>

<CURL>

```bash
curl --location --request GET 'https://api.demo.frentecorretora.com.br/v1/exchanges/paper-money/quotations/WL-FRENTE-SP?currency=USD&value=20000&reverse=true'
```

</CURL>

### Response

```json
Status: 200 OK

{
  "id": "9aa26c09265a73aa7b30e7173b6f8358a099450f",
  "reverse": true,
  "purposeCode": "IR003",
  "currency": {
    "countryFlagUrl": "https://s3.amazonaws.com/frente-exchanges/flags/united-states.svg",
    "code": "USD",
    "name": "Dólar Americano",
    "coverageRatePercentage": 89,
    "offer": 184,
    "offerUSD": {
      "value": 1840000,
      "divisor": 10000
    },
    "parityFromUSD": {
      "value": 10000,
      "divisor": 10000
    },
    "parityToUSD": {
      "value": 10000,
      "divisor": 10000
    },
    "spreadPercentage": 2.52,
    "maxToSell": 65320,
    "minToSell": 184,
    "multiples": [
      20,
      50,
      100
    ],
    "commercialExchangeRate": {
      "value": 38360,
      "divisor": 10000
    },
    "levelingRate": {
      "value": 72500,
      "divisor": 10000
    }
  },
  "tax": {
    "iof": {
      "percentage": 1.1,
      "total": {
        "value": 1504,
        "divisor": 100
      }
    }
  },
  "price": {
    "withoutTax": {
      "value": 74327,
      "divisor": 10000
    },
    "withTax": {
      "value": 75145,
      "divisor": 10000
    }
  },
  "total": {
    "withoutTax": {
      "value": 136762,
      "divisor": 100
    },
    "withTax": {
      "value": 138267,
      "divisor": 100
    }
  },
  "createdAt": "2019-11-06T14:18:57.572Z",
  "expiresAt": "2019-11-06T14:28:57.000Z",
  "timeToLive": 600,
  "merchantId": "WL-FRENTE-SP",
  "rounding": {
    "method": "MINIMUM",
    "rounded": true
  }
}
```

</Example>

</Block>
