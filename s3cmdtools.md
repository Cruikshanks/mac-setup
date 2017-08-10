# S3cmd tools

[S3cmd tools](http://s3tools.org/s3cmd) is a free command line tool and client for uploading, retrieving and managing data in Amazon S3 and other cloud storage service providers that use the S3 protocol, such as Google Cloud Storage or DreamHost DreamObjects.

## Install

```bash
brew install s3cmd
```

## Use

To authenticate with a bucket you'll need its access key and secret key. These will then need to be passed in as arguments each time you call **S3cmd**. To list what's in a bucket for example

```bash
s3cmd --access_key=UJUJUJU34344EDCOLM --secret_key=VBdsfjh875345MUTYguuiDC868689 ls s3://my-s3-bucket
```

To download a file

```bash
s3cmd --access_key=UJUJUJU34344EDCOLM --secret_key=VBdsfjh875345MUTYguuiDC868689 get s3://my-s3-bucket/name-of-file.tar.gz.enc
```

To upload a file

```bash
s3cmd --access_key=UJUJUJU34344EDCOLM --secret_key=VBdsfjh875345MUTYguuiDC868689 put myfile.tar.gz.enc s3://my-s3-bucket
```

For full details checkout <http://s3tools.org/usage>

