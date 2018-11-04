# Define as builder to use in the next step.
FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
CMD npm run build

FROM nginx
# Expose port 3000
EXPOSE 3000
# Copy NGINX config file
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf 
# Copy build project into NGINX directory
COPY --from=builder /app/build /user/share/nginx/html