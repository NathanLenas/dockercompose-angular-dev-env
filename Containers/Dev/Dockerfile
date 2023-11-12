FROM codercom/code-server

USER root

# Install Node.js and npm
RUN curl -sL https://deb.nodesource.com/setup_18.x | bash -
RUN apt-get install -y nodejs

# Install Angular CLI
RUN npm install -g @angular/cli

USER coder

EXPOSE 4200