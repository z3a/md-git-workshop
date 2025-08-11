# Use an official node image as a parent image
FROM node:23

# Set environment variables for versions
ARG USERNAME="markdown"
ARG USER_UID=2000
ARG USER_GID=$USER_UID

# Install dependencies
RUN groupadd --gid $USER_GID $USERNAME && \
    useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME && \
    apt-get update && \
    apt-get install -y ca-certificates openssl git curl wget && \
    rm -rf /var/lib/apt/lists/*

# Add Google Chrome repository
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list

# Install Chrome
RUN apt-get update && apt-get -y install google-chrome-stable

# Default shell
USER $USERNAME

# Set the default shell to bash rather than sh
ENV SHELL /bin/zsh

ENTRYPOINT [ "/bin/zsh" ]
CMD ["-l"]