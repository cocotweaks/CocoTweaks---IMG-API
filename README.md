API URL
-----------
https://ai.cococtweaks.net/img/api/

Function
-----------
Currently, it will only resize image best to fit. Maybe add more function in the future.

Parameter
-----------

All of the paramter is required, otherwise server will return error message.

### ImageUrl
The url of image. Accept png, jpg and gif, and the file which not larger than 500MB.

### Width
The width of resized image. Must be integer.

### Height
The height of resized image. Must be integer.

Usage
-----------

You can call the API to resize image with post method. Currently it only accept remote image.

Get cropped image by GET method:

You can just use the this url to crop the image. This method will return an cropped image directly, not JSON result.

https://ai.cococtweaks.net/img/api/?imageUrl={image_url}&width={image_width}&height={image_height}


Get cropped image by POST method:

```js
fetch('https://apiserver.com', {
  body:JSON.stringify({
    width: 500,
    height: 300,
    imageUrl: 'http://example.com/image.png',
  }),
  headers: {
    'content-type': 'application/json',
  },
  method: 'POST',
})
.then(response => response.json())
.then((result) =>{
  console.log(result);
});
```

If everything is OK, it will return a JSON which contain status and cropped image data (Data url of resized image):

```js
{ status: 'Success',
  cropped_image_data:
   '/9j/4AAQSkZJRgABAQAAAQABAAD//gA7Q1JFQVRPUjogZ2QtanBlZyB2MS4wICh1c2luZyBJSkcgSlBFRyB2OTApLCBxdWFsaXR5ID0gODUK/9sAQwAFAwQEBAMFBAQEBQUFBgcMCAcHBwcPCwsJDBEPEhIRDxERExYcFxMUGhURERghGBodHR8fHxMXIiQiHiQcHh8e/9sAQwEFBQUHBgcOCAgOHhQRFB4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4eHh4e/8IAEQgBLAHWAwEiAAIRAQMRAf/EABwAAAEFAQEBAAAAAAAAAAAAAAIAAQQFBgMHCP/EABkBAQEBAQEBAAAAAAAAAAAAAAABAgMEB...' }
```
The API **will not** keep your image.

Otherwise it will return a json which contain error message. For example:
```js
{ status: 'Failed',
  error_message": 'Please provide the url of image.'}
```
