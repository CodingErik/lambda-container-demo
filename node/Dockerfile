# Stage 1: Build the Node.js application
FROM node:14 AS build
WORKDIR /app
COPY package.json ./
RUN npm install --production
COPY index.js ./

# Stage 2: Create the runtime image
FROM public.ecr.aws/lambda/nodejs:14
COPY --from=build /app ${LAMBDA_TASK_ROOT}
CMD [ "index.handler" ]
