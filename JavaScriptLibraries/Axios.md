# Axios

Axios is a simple http library. The offical documentation can be found here - <a href="https://www.npmjs.com/package/axios">https://www.npmjs.com/package/axios</a>

Using Axios in a cell is an effective way to call out to an external REST API, returning the result to a cell.

For Example.

```JavaScript
axios.get('https://api.onegov.nsw.gov.au/FuelCheckApp/v1/fuel/prices/currenttrend').then(response => {
    return response.data.filter(x => x.Code == 'U91')[0].Price;
});
```
