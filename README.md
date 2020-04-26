# Redhat 8 Administration II (Webinar) 

## ACL's 

### General 

- ls -l zeigt nach den standard Rechten ein + welches zeigt, dass ACL vorhanden sind.
- mv übernimmt standardmässig die ACL
- cp kopiert die ACL wenn die Option -p (preserve) angegeben wurde

### Examples 

```
setfacl -Rm g:consultants:rwX /shares/content
```

