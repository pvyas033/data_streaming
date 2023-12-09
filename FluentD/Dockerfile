# Use an official Fluentd image as the base image
FROM fluent/fluentd:v1.11-debian-1

# Switch to the root user to install gems
USER root

# Install the New Relic Fluentd plugin
RUN gem install fluent-plugin-newrelic
RUN gem install fluent-plugin-kafka

# Copy your Fluentd configuration file into the container
COPY --chown=fluent:fluent fluent.conf /fluentd/etc/fluent.conf

# Set permissions for the configuration file
RUN chmod 644 /fluentd/etc/fluent.conf

# Expose the Fluentd port (optional, adjust if needed)
EXPOSE 24224

# Start Fluentd with your custom configuration file
CMD ["fluentd", "-c", "/fluentd/etc/fluent.conf"]