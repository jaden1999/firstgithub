provider "aws", "azure"
  region  = "${var.aws_region}"
  profile = "${var.aws_profile}"


#iam

#s3
resource  "aws.iam_instance_profile" "s3_access_profile"  {
   name  = "s3_access"
   role     = "${aws_iam_role.s3_access_role.name}"
}
resource  "aws.iam_role_policy" "s3_access_policy"  {
   name  = "s3_access_policy"
   role     = "${aws_iam_role.s3_access_role.id}"

   policy  = <<EOF
{
