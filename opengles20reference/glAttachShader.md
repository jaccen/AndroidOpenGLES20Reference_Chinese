## Name

***glAttachShader***  — attach a shader object to a program object

将一个着色器（Shader）对象绑定（Attach）到一个程序（Program）对象。

## C Specification

`void glAttachShader(GLuint program,GLuint shader);`

## Android SPecification

`void glAttachShader (int program, int shader)`

## Parameters

* ***C program*** Specifies the program object to which a shader object will be attached.


* ***C shader*** Specifies the shader object that is to be attached.



* ***Android program*** 指定着色器对象将要绑定到的程序对象。
* ***Android shader*** 指定要绑定的着色器对象。

## Description

In order to create an executable, there must be a way to specify the list of things that will be linked together. Program objects provide this mechanism. Shaders that are to be linked together in a program object must first be attached to that program object. glAttachShader attaches the shader object specified by shader to the program object specified by program. This indicates that shader will be included in link operations that will be performed on program.

All operations that can be performed on a shader object are valid whether or not the shader object is attached to a program object. It is permissible to attach a shader object to a program object before source code has been loaded into the shader object or before the shader object has been compiled. Multiple shader objects of the same type may not be attached to a single program object. However, a single shader object may be attached to more than one program object. If a shader object is deleted while it is attached to a program object, it will be flagged for deletion, and deletion will not occur until glDetachShader is called to detach it from all program objects to which it is attached.

为了创建一个可执行程序，必须找到一种方法来指定一个列表，指明将要把哪些东西连接到一起。程序对象则提供了这样的功能。首先，我们需要将一个与程序对象连接在一起的着色器对象绑定到这个程序对象上。`glAttachShader` 的功能就是将由`shader`指定的着色器对象绑定到由`program`指定的程序对象上。这说明`shader`将会被包含在`program`上进行的连接操作中。

所有能在着色器对象上进行的操作都是合法的，无论着色器对象是否绑定到程序对象上。在源代码被载入到着色器对象之前，或者在着色器对象被编译之前，将着色器对象绑定到程序对象都是合法的。向一个应用程序对象绑定同一类型的多个着色器对象也是合法的，因为它们中的每一个都可以包含完整的着色器对象的一部分。将一个着色器对象绑定到多个应用程序对象也是合法的。如果一个着色器对象在它被绑定到一个程序对象时被删除了，那么，它将被标记为删除状态，而在调用 `glDetachShader` 方法来将它从所有它绑定到的程序对象分离之前是不会进行删除的。

## Errors

`GL_INVALID_VALUE` is generated if either program or shader is not a value generated by OpenGL.

`GL_INVALID_OPERATION` is generated if program is not a program object.

`GL_INVALID_OPERATION` is generated if shader is not a shader object.

`GL_INVALID_OPERATION` is generated if shader is already attached to program, or if another shader object of the same type as shader is already attached to program.

* 如果 `program` 或 `shader`不是由 OpenGL ES 产生的，则产生 `GL_INVALID_VALUE`错误。
* 如果 `program`不是一个程序对象，或者`shader`不是一个着色器对象，则产生`GL_INVALID_OPERATION`错误。
* 如果`shader`已经绑定到了`program`对象，则产生 `GL_INVALID_OPERATION`错误。