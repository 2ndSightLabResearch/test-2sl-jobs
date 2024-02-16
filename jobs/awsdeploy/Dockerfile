# syntax=docker/dockerfile:1

# https://github.com/tradichel/SecurityMetricsAutomation
# job-awsenvinit/Dockerfile
# author: @tradichel @2ndsightlab
# description: Deploys minimal resources required for a 
# 2SL Job Execution Environment.
# Run this job first:
# https://github.com/tradichel/2sl-job-awsorginit
##############################################################

FROM public.ecr.aws/amazonlinux/amazonlinux:2023

#update the container and install packages
RUN yum update -y
RUN yum install unzip -y
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
RUN unzip awscliv2.zip
RUN ./aws/install
RUN aws --version
RUN yum remove unzip -y
RUN yum install jq -y

WORKDIR /job
#the contexts are passed in when the container is built
#using the /aws/scripts/build.sh file in the
#2sl-jobexecframeworkrepo
COPY --from=framework job/ /job/
COPY --from=framework resources /job/resources/
COPY --from=framework shared /job/shared/
COPY --from=framework job/run.sh /job/run.sh
COPY --from=job execute.sh /job/execute.sh
RUN chmod -R 755 /job

ENTRYPOINT ["/job/run.sh"]
#################################################################################
# Copyright Notice
# All Rights Reserved.
# All materials (the “Materials”) in this repository are protected by copyright 
# under U.S. Copyright laws and are the property of 2nd Sight Lab. They are provided 
# pursuant to a royalty free, perpetual license the person to whom they were presented 
# by 2nd Sight Lab and are solely for the training and education by 2nd Sight Lab.
#
# The Materials may not be copied, reproduced, distributed, offered for sale, published, 
# displayed, performed, modified, used to create derivative works, transmitted to 
# others, or used or exploited in any way, including, in whole or in part, as training 
# materials by or for any third party.
#
# The above copyright notice and this permission notice shall be included in all 
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, 
# INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A 
# PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT 
# HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION 
# OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE 
# SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
################################################################################

