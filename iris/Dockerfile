ARG IMAGE=intersystemsdc/iris-community:latest
FROM $IMAGE

USER root   
        
WORKDIR /opt/irisbuild
RUN chown ${ISC_PACKAGE_MGRUSER}:${ISC_PACKAGE_IRISGROUP} /opt/irisbuild
USER ${ISC_PACKAGE_MGRUSER}

COPY --chown=${ISC_PACKAGE_MGRUSER}:${ISC_PACKAGE_IRISGROUP} swagger swagger
#COPY --chown=${ISC_PACKAGE_MGRUSER}:${ISC_PACKAGE_IRISGROUP} module.xml module.xml
COPY --chown=${ISC_PACKAGE_MGRUSER}:${ISC_PACKAGE_IRISGROUP} iris.script iris.script
RUN chmod +x iris.script

RUN iris start IRIS && iris session IRIS < iris.script && iris stop IRIS quietly
