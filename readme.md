## gulp-query-compress
Plugin for [gulp-query](https://github.com/gulp-query/gulp-query)

Compress your images in other directory

Uses [imagemin](https://www.npmjs.com/package/imagemin),
[pngquant](https://www.npmjs.com/package/imagemin-pngquant) for PNG and
[pngquant](https://www.npmjs.com/package/imagemin-mozjpeg) for JPEG

This plugin provides automatic compress and copy.

```
npm install gulp-query gulp-query-compress
```

### Example
Paste the code into your `gulpfile.js` and configure it
```javascript
let build = require('gulp-query')
  , compress = require('gulp-query-compress')
;
build((query) => {
    query.plugins([compress])

      // simple
      .compress('src/icons/*.png','images/')

      // multi
      .compress([
        'src/icons/*.png',
        {from:'src/bg/*',to: 'bg/'},
        {from:'src/bg2/*',to: 'bg2/'}
       ], 'images/','admin')
       
      // multi and config
      .compress([
        'src/icons/*.png',
        {from:'src/bg/*',to: 'bg/'},
        {from:'src/bg2/*',to: 'bg2/'}
       ], 'images/',{
         png: {
           quality: '60-70',
           speed: 1
         }
       })

      // object
      .compress({
        name: 'any',
        from: ['src/images/*.jpg'],
        to: 'images/',
        png: {
          quality: '60-70',
          speed: 1
        },
        jpeg: {
          quality: 60,
        }
      })
    ;
});
```
And feel the freedom
```
gulp
gulp --production // For production (minification)
gulp watch // Watching change
gulp compress // Only for compress
gulp compress:admin // Only for task with name admin
...
```

### Options
```javascript
.compress({
    name: "task_name", // For gulp js:task_name 
    from: 'src/images/*.jpg', // ["src/images/*.jpg", "src/images2/*.jpg"]
    to: "images/",
    png: {
      quality: '60-70',
      speed: 1
    },
    jpeg: {
      quality: 60,
    }
})
```