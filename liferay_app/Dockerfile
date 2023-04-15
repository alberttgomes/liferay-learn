FROM liferay/portal:7.4.3.69-ga69

# Author application
LABEL "com.dashboard"=${AUTHOR}

RUN mkdir -p $LIFERAY_HOME/artifacts \
    mkdir -p $LIFERAY_HOME/artifacts/license

# Owner directory $LIFERAY
USER liferay

# Directory Liferay Portal
WORKDIR /opt/liferay/

# Copy configuration portal to into container Liferay Portal 7.4
COPY --chown=liferay:liferay configs/local/portal-ext.properties $LIFERAY_HOME/
COPY --chown=liferay:liferay configs/local/license $LIFERAY_HOME/artifacts/license
COPY --chown=liferay:liferay scripts/liferay-entrypoint.sh $LIFERAY_HOME/liferay-entrypoint.sh

# Expose ports to Liferay Portal
EXPOSE 8000 8080 8081 8088

# Executable to move frontend jar to into deploy folder
ENTRYPOINT ["/opt/liferay/liferay-entrypoint.sh"]