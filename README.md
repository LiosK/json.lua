# LiosK/json.lua

Tiny JSON Encoder in Pure Lua

## Usage

```lua
local json = require "json"
print(json.encode({ name = "John", age = 24 })) --> '{"age":24,"name":"John"}'
```

You can call subfunctions directly if you know what you are encoding:

```lua
print(json.encode_string("hello world")) --> '"hello world"'

local tbl = { "A", "B", "C", key = "value" }
print(json.encode_array(tbl))   --> '["A","B","C"]'
print(json.encode_object(tbl))  --> '{"1":"A","2":"B","3":"C","key":"value"}'
```

Or, override the behavior if you want:

```lua
print(json.encode({})) --> '[]'

json.encode_empty_table = function(_) return "{}" end

print(json.encode({})) --> '{}'
```

## Provided functions

```lua
-- primary function
json.encode(value)

-- subfunctions by `type(value)`
json.encode_nil(value)
json.encode_boolean(value)
json.encode_number(value)
json.encode_string(value)
json.encode_table(value)

-- invoked by `json.encode_table(value)`
json.encode_empty_table(value)
json.encode_array(value)
json.encode_object(value)

-- error handler for unknown `type(value)`
json.encode_other(value)
```

## License

Copyright 2020 LiosK

Licensed under the Apache License, Version 2.0 (the "License"); you may not use
this file except in compliance with the License. You may obtain a copy of the
License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed
under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR
CONDITIONS OF ANY KIND, either express or implied. See the License for the
specific language governing permissions and limitations under the License.
