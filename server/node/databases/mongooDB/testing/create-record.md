The following examples shows how to add a record through `.save()` and test it through the method `isNew`.
```js
const assert = require('assert');
const User = require('../src/user');

describe('Creating records', () => {
  it('saves a user', (done) => {
    /*
      We create a new instance
      User represents all models
      If you state 'new' it becomes a new instance
      The object you pass, will be attached to the instance
    */
    const joe = new User({ name: 'Joe' });

    // Then we save the instance to the DB
    joe.save()
      .then(() => {
        /* We test whether it is saved
          isNew is a property to check whether it is in the database
          if isNew === false it saved to the database
        */
        assert(!joe.isNew);
        done();
      });
  });
});
```
