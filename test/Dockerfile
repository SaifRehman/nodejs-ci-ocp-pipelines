FROM registry.access.redhat.com/ubi8/nodejs-16

# Install OpenJDK 17
RUN apt-get update && apt-get install -y openjdk-17-jdk wget unzip && rm -rf /var/lib/apt/lists/*

# Set JAVA_HOME environment variable
ENV JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
ENV PATH="$JAVA_HOME/bin:${PATH}"

RUN npm install -g sonar-scanner

# Verify installs
RUN node --version && java -version && sonar-scanner --version

WORKDIR /app
COPY . .

RUN npm install

CMD ["node", "index.js"]
