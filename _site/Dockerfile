# Use Ruby 3.1 as the base image
FROM ruby:3.1

# Install dependencies for Jekyll and build tools
RUN apt-get update && apt-get install -y build-essential nodejs

# Create and set working directory
WORKDIR /usr/src/app

# Copy Gemfile and Gemfile.lock first (for caching)
COPY Gemfile Gemfile.lock ./

# Install gems (this will be cached unless Gemfile changes)
RUN bundle install

# Copy the rest of your site files
COPY . .

# Expose port 4008
EXPOSE 4008

# Default command to run Jekyll server
CMD ["bundle", "exec", "jekyll", "serve", "--host", "0.0.0.0", "--port", "4008"]
