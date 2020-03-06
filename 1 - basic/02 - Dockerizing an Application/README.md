# 02 - Dockerizing an Application 


Exercises:

    - Dockerfile is just a convention
    - The Docker Hub
    - Understanding build contexts / working directories
    - Difference between COPY and ADD
    - Difference between shell-form and exec-form  CMD RUN
    - Copying files and directories


Lab Details

01 - Create an application (max ~ 30 mins)
02 - Dockerizing your application  (max ~ 20 mins)
    
# Lab Details

## 01 - Create an app

    You have a maximum of 30 mins to create a basic application in the program language of your choice.
    I would recommend python, golang or if you are one of these cool kids rust.

    A basic web hello world would be sufficient - but you are open to your own creative license in the time allocated

    The one requirement: It that can can be run with a command


    Some examples that you can use for inspiration:
    
    - https://github.com/grpc/grpc-go/tree/master/examples/helloworld (golang grpc)

    - https://github.com/aio-libs/aiohttp-demos (python async http server)

      There is even has a graphql example

    Basic example from: https://github.com/aio-libs/aiohttp

    ```
        # examples/server_simple.py
        from aiohttp import web

        async def handle(request):
            name = request.match_info.get('name', "Anonymous")
            text = "Hello, " + name
            return web.Response(text=text)

        async def wshandle(request):
            ws = web.WebSocketResponse()
            await ws.prepare(request)

            async for msg in ws:
                if msg.type == web.WSMsgType.text:
                    await ws.send_str("Hello, {}".format(msg.data))
                elif msg.type == web.WSMsgType.binary:
                    await ws.send_bytes(msg.data)
                elif msg.type == web.WSMsgType.close:
                    break

            return ws


        app = web.Application()
        app.add_routes([web.get('/', handle),
                        web.get('/echo', wshandle),
                        web.get('/{name}', handle)])

        if __name__ == '__main__':
            web.run_app(app)
    ```


## 02 - Dockerizing your application

### a.

   Write a Dockerfile to run your application using ubuntu as your base image

   *I would recommend trying to do this from scratch without any web help*

   (A tad harder that it seems - you will make typos/makes but you will learn)

### b.

    Ensure the docker can be built 

    `docker build`

### c.

    Tag your docker image


### d. 

    Push your docker image to a repository







