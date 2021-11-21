# Cross-platform headers for OS dependent functions

---

## `COMiC_OS_GetPlatformName`

`const char *` | string contains name of OS; editing not allowed
---------------|------------------------------------------------

Returns OS name.

## `_COMiC_OS_Instance`

Struct contains separate for COMiC instances OS dependent data needs for using OS API.

Defined in `_os.h` by implementation libs.

## `_COMiC_OS_Init`

`int` | `0` on success and any other value on fail
------|---------------------------------------------------------------------

Inits global OS dependent data.

## `_COMiC_OS_IsInited`

`COMiC_bool` | `0` on true otherwise non-zero value
-------------|---------------------------------------------------------------------

Check if global OS dependent data is inited.

## `_COMiC_OS_Finalize`

`void`       | no return
-------------|---------------------------------------------------------------------
`COMiC_OS *` | pointer to storage allocated for os dependent data; must be not-null

Finalize global OS dependent data.

## `_COMiC_OS_GlobalLock_Release`

`void` | no return
-------|----------

Releases global mutex after accessing OS dependent data.

## `_COMiC_OS_Instance_Init`

`void` | no return
-------|----------

Inits OS dependent data for COMiC instance.

## `_COMiC_OS_Instance_Finalize`

`void` | no return
-------|----------

Finalize OS dependent data in COMiC instance.

## `_COMiC_OS_GlobalLock_Acquire`

`void` | no return
-------|----------

Acquires global mutex for accessing OS dependent data.

## `COMiC_OS_Time`

type           | name         | comment
---------------|--------------|--------
`COMiC_int16`  | year         |
`COMiC_uint8`  | month        |
`COMiC_uint8`  | day          |
`COMiC_uint8`  | hour         |
`COMiC_uint8`  | minute       |
`COMiC_uint8`  | second       |
`COMiC_uint16` | milliseconds |

Structure represents time

## `COMiC_OS_GetTime`

`COMiC_OS_Time` | structure represents time
----------------|---------------------------------------------------------------------

Returns current global time.

## `COMiC_OS_Thread`

Struct contains OS dependent data needs for thread.

Defined in `_os.h` by implementation libs.

## `COMiC_OS_Thread_Create`

`int`                       | `0` on success and any other value on fail
----------------------------|---------------------------------------------------------------------
`COMiC_OS_Thread *`         | pointer to storage allocated for thread os dependent data; must be not-null
`void *(*func)(void *data)` | pointer to function that will run in thread; must be not-null
`void *data`                | pointer that will be passed to `func`; may be null

Creates thread that will run `func`.

Paused after creation, resume needed.

## `COMiC_OS_Thread_Pause`

`int`               | `0` on success and any other value on fail
--------------------|---------------------------------------------------------------------
`COMiC_OS_Thread *` | pointer to storage allocated for thread os dependent data; must be not-null

Pauses thread.

## `COMiC_OS_Thread_Resume`

`int`               | `0` on success and any other value on fail
--------------------|---------------------------------------------------------------------
`COMiC_OS_Thread *` | pointer to storage allocated for thread os dependent data; must be not-null

Resumes thread.

## `COMiC_OS_Thread_Wait`

`int`               | `0` on success and any other value on fail
--------------------|---------------------------------------------------------------------
`COMiC_OS_Thread *` | pointer to storage allocated for thread os dependent data; must be not-null
`COMiC_uint32`      | milliseconds to waits

Waits not greater then `millisecinds` (if > 0) to thread ended.

## `COMiC_OS_Thread_Kill`

`int`               | `0` on success and any other value on fail
--------------------|---------------------------------------------------------------------
`COMiC_OS_Thread *` | pointer to storage allocated for thread os dependent data; must be not-null

Kills thread (but not destroys).

## `COMiC_OS_Thread_Destroy`

`void`              | `0` on success and any other value on fail
--------------------|---------------------------------------------------------------------
`COMiC_OS_Thread *` | pointer to storage allocated for thread os dependent data; must be not-null

Unregisters and destroys thread.

## `COMiC_OS_Thread_RegisterCurrent`

`int`               | `0` on success and any other value on fail
--------------------|---------------------------------------------------------------------
`COMiC_OS *`        | pointer to OS instance
`COMiC_OS_Thread *` | pointer to storage allocated for thread os dependent data; must be not-null

Registers invoker thread.

## `COMiC_OS_Thread_Unregister`

`void`              | `0` on success and any other value on fail
--------------------|---------------------------------------------------------------------
`COMiC_OS_Thread *` | pointer to storage allocated for thread os dependent data; must be not-null

Unregisters thread.

## `COMiC_OS_Thread_GetCurrent`

`COMiC_OS_Thread *` | returns pointer to thread storage or `NULL` if it is not registered
--------------------|---------------------------------------------------------------------

Returns invoker thread if it is registered.

## `COMiC_OS_Error`

type               | name        | comment
-------------------|-------------|------------------------------------------------
`const char *`     | message     |
`voif (*)(char *)` | deallocator | used to free message if it is in dynamic buffer

Structure for storing errors.

## `COMiC_Error_Set`

`void`         | no return
---------------|--------------
`const char *` | error message

Sets error.

## `_COMiC_Error_Set`

`void`          | no return
----------------|--------------
`COMiC_Error *` | error storage
`const char *`  | error message

Sets error to specified storage.

## `COMiC_Error_SetHeap`

`void`             | no return
-------------------|--------------
`void (*)(char *)` | deallocator
`const char *`     | error message

Sets error with deallocator to free message string.

## `_COMiC_Error_SetHeap`

`void`             | no return
-------------------|--------------
`COMiC_Error *`    | error storage
`void (*)(char *)` | deallocator
`const char *`     | error message

Sets error to specified storage.

## `COMiC_Error_Get`

`const char *` | error message or `NULL` if not set
---------------|-----------------------------------

Returns current error message or if set.

## `_COMiC_Error_Get`

`const char *`  | error message or `NULL` if not set
----------------|-----------------------------------
`COMiC_Error *` | error storage

Returns current error message from specified storage if set.

## `COMiC_Error_Clear`

`void` | no return
-------|----------

Clears error message.

## `_COMiC_Error_Clear`

`void`          | no return
----------------|----------
`COMiC_Error *` | error storage

Clears error message in specified storage.

## `COMiC_Alloc`

`void *`     | pointer to allocated buffer
-------------|----------------------------
`COMiC_size` | buffer size

Allocates buffer in local heap.

## `COMiC_Calloc`

`void *`     | pointer to allocated buffer
-------------|----------------------------
`COMiC_size` | elems count
`COMiC_size` | elem size

Allocates buffer in local heap.

## `COMiC_ReAlloc`

`void *`     | pointer to allocated buffer
-------------|----------------------------
`void *`     | pointer to buffer to realloc
`COMiC_size` | new buffer size

Reallocates buffer in local heap.

## `COMiC_ReCalloc`

`void *`     | pointer to allocated buffer
-------------|----------------------------
`void *`     | pointer to buffer to realloc
`COMiC_size` | elems count
`COMiC_size` | elem size

Reallocates buffer in local heap.

## `COMiC_Free`

`void`     | no return
-----------|----------------------------
`void *`   | pointer to buffer to realloc

Deallocates buffer in local heap.

## `COMiC_OS_Lock_Create`

`int`          | `0` on success and any other value on fail
---------------|----------------------------
`COMiC_Lock *` | pointer to mutex storage

Inits mutex in specified storage.

## `COMiC_OS_Lock_Lock`

`int`          | `0` on success and any other value on fail
---------------|----------------------------
`COMiC_Lock *` | pointer to mutex storage

Tries to acquire mutex.

## `COMiC_OS_Lock_Unlock`

`void`         | no return
---------------|----------------------------
`COMiC_Lock *` | pointer to mutex storage

Releases mutex.

## `COMiC_OS_Lock_Destroy`

`void`         | no return
---------------|----------------------------
`COMiC_Lock *` | pointer to mutex storage

Destroys mutex.