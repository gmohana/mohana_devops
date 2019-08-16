provider "aws"{
  # Credentials to access aws cluster
  access_key = "${var.access_key}"
  secret_key = "${var.secret_key}"
  region = "${var.region}"
}

resource "aws_instance" "test-inst" {
  instance_type = "${var.instance_type}"
  ami           = "${var.ami}"
  count         = "${var.count_i}"
# vpc_id        = "${var.vpcid}" # Not required, subnet id will pick vpc_id
  subnet_id     = "${var.subnet_id}"
  vpc_security_group_ids = "${var.security_group_id}"
  associate_public_ip_address = "${var.associate_public_ip_address}"
}
 
