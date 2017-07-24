FROM alleen/apq8016_bm

# We need this because of this https://blog.phusion.nl/2015/01/20/docker-and-the-pid-1-zombie-reaping-problem/
# Here is solution https://engineeringblog.yelp.com/2016/01/dumb-init-an-init-for-docker.html
RUN curl --create-dirs -sSLo /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v1.1.3/dumb-init_1.1.3_amd64
RUN chmod +x /usr/local/bin/dumb-init

RUN echo "export USE_CCACHE=1" >> /etc/profile.d/android
ENV USE_CCACHE 1
ENV CCACHE_DIR /ccache

WORKDIR /RSB4760_advantech

CMD ["/usr/local/bin/dumb-init", "--", "/RSB4760_advantech/apq8016_build.sh", ";", "chmod", "-R", "777", "/RSB4760_advantech/out"]
