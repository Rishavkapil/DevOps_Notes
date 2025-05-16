

The file provisioner is used to copy files or directories from the machine executing Terraform to the newly created resource. The file provisioner supports both ssh and winrm type connections.

let's modify instance.tf file to use file provisioner. and also create a readme.md file with any content because we are going to copy that file to remote instance


```sh
resource "aws_instance" "web" {
  ami                    = data.aws_ami.ubuntu.id
  instance_type          = var.instance_type
  key_name               = aws_key_pair.key-tf.key_name
  vpc_security_group_ids = ["${aws_security_group.allow_tls.id}"]
  tags = {
    Name = "first-tf-instance"
  }
  user_data = file("${path.module}/script.sh")
  connection {
    type        = "ssh"
    user        = "ubuntu"
    private_key = file("${path.module}/id_rsa")
    host        = self.public_ip
  }
  # file, local-exec, remote-exec
  provisioner "file" {
    source      = "readme.md"      # terraform machine
    destination = "/tmp/readme.md" # remote machine
  }
  provisioner "file" {
    content     = "this is test content" # terraform machine
    destination = "/tmp/content.md"      # remote machine
  }
}
```



## Directory Uploads

The file provisioner is also able to upload a complete directory to the remote machine. When uploading a directory, there are a few important things you should know.

First, when using the ssh connection type the destination directory must already exist. If you need to create it, use a remote-exec provisioner just prior to the file provisioner in order to create the directory.

If the source is /foo (no trailing slash), and the destination is /tmp, then the contents of /foo on the local machine will be uploaded to /tmp/foo on the remote machine. The foo directory on the remote machine will be created by Terraform.

If the source, however, is /foo/ (a trailing slash is present), and the destination is /tmp, then the contents of /foo will be uploaded directly into /tmp.

This behavior was adopted from the standard behavior of [rsync](https://linux.die.net/man/1/rsync).


```sh
# Copy a directory

  provisioner "file" {
    source = "conf"
    destination = "/home/ec2-user"

  }
```

