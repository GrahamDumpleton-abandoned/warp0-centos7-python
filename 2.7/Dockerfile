FROM centos/python-27-centos7

MAINTAINER Graham Dumpleton <Graham.Dumpleton@gmail.com>

ENV WARPDRIVE_VERSION=0.19.2 \
    PYTHON_VERSION=2.7.11 \
    MOD_WSGI_VERSION=4.5.0

RUN curl -SL -o /opt/app-root/getwarped.sh https://raw.githubusercontent.com/GrahamDumpleton/warpdrive/master/getwarped.sh \
    && source scl_source enable python27 \
    && sh -x /opt/app-root/getwarped.sh --version $WARPDRIVE_VERSION

ENV STI_SCRIPTS_PATH=/opt/app-root/s2i/bin \
    STI_SCRIPTS_URL=image:///opt/app-root/s2i

LABEL io.k8s.description="S2I builder for Python web applications (CentOS 7)." \
      io.k8s.display-name="Python 2.7 (Warp Drive - CentOS 7)" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="builder,python,python27,warpdrive,warpdrive-python27" \
      io.openshift.s2i.scripts-url="image:///opt/app-root/s2i/bin" \
      io.s2i.scripts-url=image:///opt/app-root/s2i

ENTRYPOINT [ "warpdrive", "exec" ]
CMD [ "warpdrive", "start" ]
