# Crypto-Currency-Rates-API-Go
This repository is used to retrieve the list of currencies using WestinPay's API which provides the list of currencies.
## WestinPay Crypto Currency Go Code

```Go
package main

import (
    "fmt"
    "io/ioutil"
    "net/http"
)

func main() {
    apiKey := "your_api_key"
    base := "BTC"
    output := "JSON"
    url := fmt.Sprintf("https://westinpay.com/currency/crypto_api?api_key=%s&base=%s&output=%s", apiKey, base, output)

    resp, err := http.Get(url)
    if err != nil {
        fmt.Println("Error:", err)
        return
    }
    defer resp.Body.Close()

    body, err := ioutil.ReadAll(resp.Body)
    if err != nil {
        fmt.Println("Error:", err)
        return
    }

    fmt.Println(string(body))
}
