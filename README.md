
## Welcome to my profile!

### FAQ:
Q:  What's my favorite language?
A: 
```cpp
#include  <iostream>

void fmtprint_internal(const char *str) {
    std::cout << str;
}

template <class T, class... Targs>
void fmtprint_internal(size_t strlen, const char *str, const T& data1, const Targs&... datarest) {
    for (int i = 0; i < strlen - 1; i++) {
        char c1 = str[i];
        char c2 = str[i + 1];

        if (c1 == '{' && c2 == '}') {
            std::cout << data1;
            if constexpr (sizeof... (datarest) == 0) fmtprint_internal(&str[i + 2]);
            else fmtprint_internal(strlen - i, &str[i + 2], datarest...);
            return;
        }
        std::cout << c1;
    }
}

template <class... Targs>
void fmtprint(const char *str, const Targs&... data) {
    if constexpr (sizeof... (data) == 0) {
        return fmtprint_internal(str);
    }
    else {
        size_t strlen = 0;
        for (char c = str[strlen]; c != 0; strlen++, c = str[strlen]);

        fmtprint_internal(strlen, str, data...);
    }
}

int main() {
	fmtprint("{} is the best language ever.\n", "C++");
	return 0;
}
```
