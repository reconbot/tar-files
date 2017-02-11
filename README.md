tar-files
---------

[![Greenkeeper badge](https://badges.greenkeeper.io/reconbot/tar-files.svg)](https://greenkeeper.io/)

convenience wrapper around fs gunzip and node-tar to stream file entries' data.

```js
var te = require('tar-files')
var eos = require('end-of-stream')

te('package.tar',function(stream,cb){
  if(stream.path === "package/README.md") {
    eos(stream.pipe(fs.createWriteStream('./tar-README.md')),cb)
  } else {
    // skip this entry
    cb();
  }
},function(err){
  
  // all done!

})

```

this example saves the `README.md` file from package.tar to the file `./tar-README.md`

- works with gzipped or not compressed tars.
