# bind

### reload zone
```
rndc reload zonename
```

### dynamic updates
Before manual edit of *zone file* dynamic updates must be disabled by
```
rndc freeze zonename
```
After edit of *zone file* dynamic updates can be enabled by issuing
```
rndc thaw zonename
```