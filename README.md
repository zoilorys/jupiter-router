# jupiter-orm-mongo

## API

### .Fabric(options)

Returns adapter API object.

**Arguments**

options - {object} - object with properties for connection.

Available options:
* host - {string} - host name without protocol, e.g. '127.0.0.1';
* port - {number} - port of host server to connect;
* database - {string} - name of DB to connect

**Example**
```javascript
let ORM = Fabric({
  host: '127.0.0.1',
  post: 27017,
  database: 'test',
});
```

## Adapter API

### .connect()

Establish connection to DB. Returns adapter object.

**Example**
```javascript
let ORM = Fabric({
  // options
});

ORM.connect();

```

### .query(collection)

Returns Query interface of adapter for selected collection.

**Arguments**

collection - {string} - name of collection to query.

**Example**
```javascript
let ORM = Fabric({
  // options
});

ORM.connect().query('test_items').find().exec().then(console.log.bind(console));

```

### .close()

Closes current connection.

**Example**
```javascript
let ORM = Fabric({
  // options
});

ORM.connect().query('test_items').find().exec().then(function(result) {
  doSomethingWith(result);
  ORM.close();
});

```

## Query API

### .find(query)

Returns Find interface for query.

**Arguments**
query - {object} - object, that contains query сonditions.

**Example**
```javascript
let ORM = Fabric({
  // options
});

ORM.connect().query('test_items').find().exec().then(console.log.bind(console));

```

## .insert(query)

Returns Insert interface for query.

**Arguments**
query - {object} - object, that contains query сonditions.

**Example**
```javascript
let ORM = Fabric({
  // options
});

ORM.connect().query('test_items').insert({name: 'test'}).exec().then(console.log.bind(console));

```

## Find API

### .order(sortOption)

Sets sorting option. Returns find interface object

**Arguments**
sortOption - {object} - object, that contains sorting options.

Object must be of type {<key>, <direction>}, where values for direction is
1 for ascending and -1 for descending.

**Example**
```javascript
let ORM = Fabric({
  // options
});

ORM.connect().query('test_items').find().order({'name': 1}).exec().then(console.log.bind(console));

```

### .limit(limitOption)

Limits number of results form query. Returns find interface object

**Arguments**
limitOption - {number} - limit for the number of returned results. 0 by default, and it equals 'no limit'.

**Example**
```javascript
let ORM = Fabric({
  // options
});

ORM.connect().query('test_items').find().limit(5).exec().then(console.log.bind(console));

```

### .exec()

Executes query and returns Promise object.

**Example**
```javascript
let ORM = Fabric({
  // options
});

ORM.connect().query('test_items').find().order({'name': -1}).limit(10).exec().then(function(result) {
  doSomethingWith(result);
  ORM.close();
});

```

## Insert API

### .exec()

Executes query and returns Promise object.

**Example**
```javascript
let ORM = Fabric({
  // options
});

ORM.connect().query('test_items').insert({name: 'test'}).exec().then(function(result) {
  doSomethingWith(result);
  ORM.close();
});

```
