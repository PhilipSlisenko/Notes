List all objects in bucket
``` python
s3 = boto3.resource('s3')
bucket = s3.Bucket('isdm-italy-mvp')
for bucket_object in bucket.objects.all():
    print(bucket_object)
bucket_object(bucket_name, key)
```