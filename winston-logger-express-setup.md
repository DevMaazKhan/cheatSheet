# Winston Logger

This is used for logging in the project, make sure you have running express server before taking these steps

1. install winston
   `npm i -S winston`
2. create a logger file, maybe in src/util/logger.ts
   `touch src/util/logger.ts`
3. add this content to the file:
   `import { createLogger, format, transports, addColors } from 'winston';
import config from './config';
const { colorize, timestamp, printf, combine } = format;
 const myCustomFormat = format.combine(
 colorize({ all: true }),
 timestamp({ format: 'hh:mm:ss A' }),
 printf((info) => `${info.timestamp} ${info.level} : ${info.message}`)
);
addColors({
info: 'bold blue', // fontStyle color
warn: 'italic yellow',
error: 'bold red',
debug: 'green',
});
const logger = createLogger({
level: config.ENV === 'production' ? 'info' : 'silly',
transports: [new transports.Console({ format: combine(myCustomFormat) })],
});
 export default logger;
 ` 4. you have a logger, call it with different log levels
