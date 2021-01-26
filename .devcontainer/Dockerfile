FROM php:7.3-apache

RUN apt-get update \
#     && apt-get install -y php php-mbstring php-mysql apache2 git mysql-server mysql-client curl
     && apt-get install -y git curl unzip \
     && docker-php-ext-install pdo_mysql mysqli mbstring \
     && a2enmod headers \
     && a2enmod rewrite

# Update args in docker-compose.yaml to set the UID/GID of the "vscode" user.
# ARG USER_UID=1000
# ARG USER_GID=$USER_UID
# RUN if [ "$USER_GID" != "1000" ] || [ "$USER_UID" != "1000" ]; then groupmod --gid $USER_GID vscode && usermod --uid $USER_UID --gid $USER_GID vscode; fi

# [Optional] Install a version of Node.js using nvm for front end dev
# ARG INSTALL_NODE="true"
# ARG NODE_VERSION="lts/*"
# RUN if [ "${INSTALL_NODE}" = "true" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# Download CakePHP
RUN cd /var/www \
  && git clone -b 2.10.24 git://github.com/cakephp/cakephp.git html 

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1

EXPOSE 80