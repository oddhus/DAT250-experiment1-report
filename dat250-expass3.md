# Software Technology Experiment Assignment 3

## Technical problems

My [Map-reduce function](#Code) first returned NaN when adding together the quantity. To fix this i needed to add this part:

```javascript
if (reducedVal[items[idx].sku] == undefined) {
  reducedVal[items[idx].sku] = 0;
}
```

## Screenshots

### Experiment 1: MongoDB CRUD operations

##### The correct validation of installation pacakage

![Image of package validation](https://github.com/oddhus/DAT250-reports/blob/master/images/install_validation.jpg)

##### CRUD operations

###### Create

![Create Documents with MongoDB](https://github.com/oddhus/DAT250-reports/blob/master/images/CreateDocuments.jpg)

###### Query

![Query Documents with MongoDB](https://github.com/oddhus/DAT250-reports/blob/master/images/QueryDocuments.jpg)

###### Update

![Update Documents with MongoDB](https://github.com/oddhus/DAT250-reports/blob/master/images/UpdateDocuments.jpg)

###### Remove

![Delete Documents with MongoDB](https://github.com/oddhus/DAT250-reports/blob/master/images/DeleteDocuments.jpg)

###### Bulk

![BulkWrite Documents with MongoDB](https://github.com/oddhus/DAT250-reports/blob/master/images/BulkWriteDocs.jpg)

### Experiment 2: Aggregation

##### Working example

![MapReduce example with MongoDB](https://github.com/oddhus/DAT250-reports/blob/master/images/MapReduceExample.jpg)

##### My Map-reduce implementation

###### Code

```javascript
var mapFunction3 = function () {
  for (var idx = 0; idx < this.items.length; idx++) {
    value = { sku: this.items[idx].sku, qty: this.items[idx].qty };
    emit(this.cust_id, value);
  }
};
```

```javascript
var reduceFunction3 = function (keyCustId, items) {
  reducedVal = {};
  for (var idx = 0; idx < items.length; idx++) {
    if (reducedVal[items[idx].sku] == undefined) {
      reducedVal[items[idx].sku] = 0;
    }
    reducedVal[items[idx].sku] += items[idx].qty;
  }
  return reducedVal;
};
```

```javascript
db.orders.mapReduce(mapFunction3, reduceFunction3, {
  out: { merge: "map_reduce_3" },
});
```

###### Result

![My MapReduce operation with MongoDB](https://github.com/oddhus/DAT250-reports/blob/master/images/MyMapReduceOperation.jpg)

###### Why is this operation useful?

My Map-reduce operation group orders by customer id and summaries their order history. The order history is summarized by grouping the items by the sku field and calculating the total quantity for each sku. This is useful for getting an overview over each individual customer, and maybe target them with specific advertisment based on their most bought products.

## Pending issues

None
