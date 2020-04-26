# Redhat 8 Administration II (Webinar) 

## ACL's 

### General 

- ls -l zeigt nach den standard Rechten ein + welches zeigt, dass ACL vorhanden sind.
- mv übernimmt standardmässig die ACL
- cp kopiert die ACL wenn die Option -p (preserve) angegeben wurde

### Examples 

```
# Set permissions for a specific group 
# recursive / add or modfify for group consultants 
setfacl -Rm g:consultants:rwX /shares/content

# Withdraw permissions for a specific user 
setfacl -Rm u:consultant1:- /shares/content

# Set default permission for a specific group 
# important for the subdirectories and the content of them
setfacl -m d:g:consultants:rwx /shares/content

```

