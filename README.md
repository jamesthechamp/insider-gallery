# insider gallery 

Simple gallery Application with each image stored in 4 optimized size:

    horizontal : 755 x 450  
    vertical : 365 x 450  
    horizontal small : 365 x 212  
    gallery : 380 x 380 

All upload image need to be of size `1024 x 1024`
## Stack Used
    AngularJS, NodeJS, ExpressJS, MongoDB
    lint: jsHint(extended airbnb standards)
    Image Storage: Cloudinary
    Logger: Morgan, winston



### demo

demo: for `image crop then upload`:

![Alt Text](./README_GIFs/demo1.gif)

demo: to see all uploaded images:

![Alt Text](./README_GIFs/demo2.gif)

demo: in case file dimension is not 1024 x 1024

![Alt Text](./README_GIFs/demo_fail.gif)

## Step to build

### Install Dependencies

We have two kinds of dependencies in this project: tools and Angular framework dependency and nodeJS packages.

* We get the nodeJS backend packages via `npm`, the [Node package manager][npm].
* We get the Angular dependency via `bower`, a [client-side code package manager][bower].

We have preconfigured `npm` to automatically run `bower` so we can simply do:

```
npm install
```

Behind the scenes this will also call `bower install`. After that, you should find out that you have
two new folders in your project.

* `node_modules` - contains the npm packages for the tools we need
* `app/bower_components` - contains the Angular framework files

### Run the Application

Project is preconfigured with dependency installation to start application run:

```
npm start
```

Now browse to the app at [`localhost:3000/`].


### APIs info  

####API 1: 

Get all images: 

    API End Point: /api/v1/images/get
    Request: {
        METHOD: ['GET'],
        header: { content-type: 'application/json'}
    }
    Response: {
        status: 'success'/'fail',
        data: [
            {
                id: <String> imageId 
                imageGallery: <String> Gallery size cropped image URL,
                imageHorizontal: <String> Horizontal size cropped image URL
                imageHorizontalSmall: <String> Horizontal small size cropped image URL
                imageVertical: <String> Vertical size cropped image URL
                created_at: <Date> timeStamp
            }
        ],
        err: "error message" (in case of error)

    }

####API 2:  

Upload Cropped Images  

    API End Point: /api/v2/images/upload
    Request: {
        METHOD: ['POST'],
        header: { content-type: 'application/json'},
        body:  
        {
            imageGallery: <Image> Gallery size cropped image,
            imageHorizontal: <Image> Horizontal size cropped image
            imageHorizontalSmall: <Image> Horizontal small size cropped image
            imageVertical: <Image> Vertical size cropped image
        }
    }
    Response: {
        status: 'success'/'fail',
        data: {
            id: <String> imageId 
            imageGallery: <String> Gallery size cropped image URL,
            imageHorizontal: <String> Horizontal size cropped image URL
            imageHorizontalSmall: <String> Horizontal small size cropped image URL
            imageVertical: <String> Vertical size cropped image URL
            created_at: <Date> timeStamp
        },
        err: "error message" (in case of error)
    }

