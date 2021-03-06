The following document provides examples of how to test different ways to delete  a record:
- Instance => through `.remove`
- Class => through `.deleteMany` 
- Class => through `.findOneAndDelete`
- Class => through `findByIdAndDelete`

<img src="../images/testing-delete-record.png" width="500">
NOTE: images still shows `remove` instead of `delete`. Terminal shows deprecation warning if I use `remove`.

```js

const assert = require('assert');
const User = require('../src/user');

describe('Deleting a user', () => {
  let joe;

  beforeEach((done) => {
    joe = new User({ name: 'Joe' });
    joe.save()
      .then(() => done());
  });

  it('model instance remove', (done) => {
    // joe is the instance you created before
    joe.remove()
      .then(() => User.findOne({ name: 'Joe' }))
      .then((user) => {
        assert(user === null);
        done();
      });
  });

  it('class method delete', (done) => {
    // Remove a bunch of records with some given criteria (e.g. multiple Joe's)
    User.deleteMany({ name: 'Joe' })
      .then(() => User.findOne({ name: 'Joe' }))
      .then((user) => {
        assert(user === null);
        done();
      });
  });

  /*
    give criteria, and the first one that is matched is removed
    user case example: remove someone based on email
  */
  it('class method findOneAndDelete', (done) => {
    User.findOneAndDelete({ name: 'Joe' })
      .then(() => User.findOne({ name: 'Joe' }))
      .then((user) => {
        assert(user === null);
        done();
      });
  });

  // remove my idea
  it('class method findByIdAndDelete', (done) => {
    User.findByIdAndDelete(joe._id)
      .then(() => User.findOne({ name: 'Joe' }))
      .then((user) => {
        assert(user === null);
        done();
      });
  });
});
```
