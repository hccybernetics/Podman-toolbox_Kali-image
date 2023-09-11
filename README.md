# Podman-toolbox_Kali-image
This Instructions will guide you to create a podman toolbox image of Kali-Linux

1 - Create a file "podmanfile.kali" with following content
*************************************************************
FROM docker.io/kalilinux/kali-rolling:latest

LABEL com.github.containers.toolbox="true" \
      com.github.debarshiray.toolbox="true"

RUN apt-get update && \
    apt-get -y install sudo libcap2-bin && \
    apt-get clean

RUN sed -i -e 's/ ALL$/ NOPASSWD:ALL/' /etc/sudoers

RUN touch /etc/localtime
RUN echo VARIANT_ID=container >> /etc/os-release

CMD /bin/bash
******************************************************************

2 - Use the following command "**podman build -t kali-toolbox -f podmanfile.kali**" to build from docker file

3 - Create the toolbox container by running "**toolbox create -i localhost/kali-toolbox:latest**"

The Work is complete
Now Lets enter the toolbox using "**toolbox enter kali-toolbox-latest**"

Note : if you got error message like "unable to resolve host" add "**127.0.0.1    toolbox**" in /etc/hosts in your host pc

This instructions can be used for other images also.


REF : https://support.endlessos.org/en/dev/toolbox-debian

# Educational and Ethical Purpose Only

