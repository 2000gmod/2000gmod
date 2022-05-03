
## Welcome to my profile!

### FAQ:
Q:  What's my favorite language?
A: 
```cpp
#include  <iostream>

void fmtprint_internal(int i, const char *str) {
    std::cout << str;
}

template <class T, class... Targs>
void fmtprint_internal(int strlen, const char *str, T data1, Targs... datarest) {
    for (int i = 0; i < strlen - 1; i++) {
        char c1 = str[i];
        char c2 = str[i + 1];

        if (c1 == '{' && c2 == '}') {
            std::cout << data1;
            fmtprint_internal(strlen - i, &str[i + 2], datarest...);
            return;
        }
        std::cout << c1;
    }
}

template <class T, class... Targs>
void fmtprint(const char *str, T data1, Targs... datarest) {
    size_t strlen = 0;
    for (char c = str[strlen]; c != 0; strlen++, c = str[strlen]);

    fmtprint_internal(strlen, str, data1, datarest...);
}

int main()  {
	fmtprint("{} is the best language\n", "C++");
	return 0;
}

```
