# Promise

Similar to JavaScript Promise

## basic
```
Promise.Apply(procedure 
begin 
  writeln('hello world');
end).Start.Wait();
```

## return value
```
Promise.Apply<string>(functon : string
begin 
  result := 'hello world'
end)
.Next.Apply<string>(procedure(const AValue : string) 
begin 
  writeln(AValue);
end).Start.Wait();
```

## accept and return value
```
Promise.Apply<string>(functon : string
begin 
  result := 'hello'
end)
.Next.Apply<string, string>(functon(const AValue : string) : string
begin 
  result := AValue + ' world'
end)
.Next.Apply(procedure(const AValue : string) 
begin 
  writeln(AValue);
end).Start.Wait();
```


## throw exception
Use Catch() to handle exceptions. Multiple Apply blocks can be used before  a catch block.
```
Promise.Apply(procedure 
begin 
  raise Exception.Create('problem');
end)
.Next.Catch(procedure(const AException : Exception) 
begin
  writeln(AException.Message);
end).Start.Wait();
```