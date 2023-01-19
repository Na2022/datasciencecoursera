R syntax
===

### Basics

```
"Hello World!"
plot(1:10)
print("Hello,world!")

for(x in 1:10)
{
  print(x)
}


name <- "John"
age <- 40
name
age
paste("My name is",name)
paste(name, age)
age2 <- 45
age+age2

x <- 9i+3
class(x)

y <- 5.0
class(y)
z <- as.integer(y)
class(z)

ceiling(1.4)
floor(1.5)

str <- "Lorem ipsum dolor sit amet"
str2 <- "Le Roid de Monde"
cat(str)
nchar(str)
grepl("ip",str)
paste(str, str2)
str3 <- "We are the so-called \"Vikings\", from the north"
cat(str3)
```
