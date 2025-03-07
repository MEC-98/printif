#include <stdio.h>
#include <stdarg.h>

int _printf(const char *format, ...)
{
    va_list args;
    int count = 0;
    
    va_start(args, format);
    
    for (const char *ptr = format; *ptr != '\0'; ptr++) {
        if (*ptr == '%') {
            ptr++;
            switch (*ptr) {
                case 'c': {
                    char c = (char)va_arg(args, int);
                    putchar(c);
                    count++;
                    break;
                }
                case 's': {
                    char *str = va_arg(args, char *);
                    if (str) {
                        while (*str) {
                            putchar(*str);
                            str++;
                            count++;
                        }
                    }
                    break;
                }
                case '%': {
                    putchar('%');
                    count++;
                    break;
                }
                default: {
                    putchar('%');
                    putchar(*ptr);
                    count += 2;
                    break;
                }
            }
        } else {
            putchar(*ptr);
            count++;
        }
    }
    
    va_end(args);
    return count;
}

// Example usage
int main() {
    _printf("Hello, %s! Today is %c day.%%\n", "world", 'G');
    return 0;
}

