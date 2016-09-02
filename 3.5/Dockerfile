FROM centos/python-35-centos7

MAINTAINER Graham Dumpleton <Graham.Dumpleton@gmail.com>

ENV WARPDRIVE_VERSION=0.23.0 \
    MOD_WSGI_VERSION=4.5.6

RUN curl -SL -o /opt/app-root/getwarped.sh https://raw.githubusercontent.com/GrahamDumpleton/warpdrive/master/getwarped.sh \
    && source scl_source enable rh-python35 \
    && sh -x /opt/app-root/getwarped.sh --version $WARPDRIVE_VERSION

ENV STI_SCRIPTS_PATH=/opt/app-root/s2i/bin \
    STI_SCRIPTS_URL=image:///opt/app-root/s2i

LABEL io.k8s.description="S2I builder for Python web applications (CentOS 7)." \
          io.k8s.display-name="Python 3.5 (Warp Drive - CentOS 7)" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="builder,python,python35,warpdrive,warpdrive-python35" \
      io.openshift.s2i.scripts-url="image:///opt/app-root/s2i/bin" \
      io.s2i.scripts-url=image:///opt/app-root/s2i

CMD [ "warpdrive", "start" ]
