# JSON
## Description
Using .json files / formatting with c++.

## nlohmann library
Comprehensive c++ library for json formatting.

Github: https://github.com/nlohmann/json

### Installation
#### Homebrew (mac)
```bash
brew install nlohmann-json
```

### Setup
Check in [releases](https://github.com/nlohmann/json/releases/tag/v3.9.1) for version specific SHA256 key and URL.

```cmake
if(UNIX AND NOT APPLE)
	CPMAddPackage(
		NAME nlohmann_json
		VERSION 3.9.0
		# Just get the latest (3.9.0) version, and only the include folder as the rep is biig
		URL https://github.com/nlohmann/json/releases/download/v3.9.0/include.zip
		URL_HASH SHA256=5b9b819aed31626aefe2eace23498cafafc1691890556cd36d2a8002f6905009
	)
elseif(APPLE)
	find_package(nlohmann_json 3.2.0 REQUIRED)
	target_link_libraries(foo PRIVATE nlohmann_json::nlohmann_json)	
endif()
```

### Usage
#### Initalise
```cpp
#include <nlohmann/json.hpp>
using json = nlohmann::json;
```

#### Construct
```cpp
json j;
```

#### Add values
```cpp
j["value_name"] = "value"; // Single value
j["value1"]["value2"] = "value"; // Nested value
```

#### Print formatted
```cpp
// n represents an interger for the number of spaces to indent 
std::cout << j.dump(n) << std::endl; 
```

#### Example output
```json
{
	"value_name": "value", 
	"value1": {
		"value2": "value"
	}
}
```

