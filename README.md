# xqual.xagent.xstudio.docker
Contains docker files for XAgent from XQual/XStudio

The Dockerfile and image files are also available from Docker HUB

These are provided as basic examples. 

You need to update the dockerfile for xagent-jav8 to include the XStudio.conf and plugin.conf files so that XAgent can find it
    * this is dependent on your XStudio instance, so we did not provide that part
    `COPY xtudio.Conf /usr/share/xqual/xstudio/xstudio.conf`
    `COPY plugin.Conf /usr/share/xqual/xstudio/plugin.conf`

Note: this is not an official delivery from XQualand is not part of the commercial soutions. 
