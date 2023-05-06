# ENV Variables in express Application

This is for typescript

1. Install Zod
   `npm i zod`
2. Install env-schema
   `npm i env-schema`
3. create a file called config in util folder,
   `touch src/util/config.ts`
4. add this in it
   import envSchema from 'env-schema';
   import zod from 'zod';

const schema = zod.object({
PORT: zod.number().default(40000),
ENV: zod.string().default('development'),
});

type Env = zod.infer<typeof schema>;

const config = envSchema<Env>({
schema: {
type: 'object',
required: [],
properties: {
PORT: {
type: 'number',
default: 40000,
},
ENV: {
type: 'string',
default: 'development',
},
},
},
dotenv: true,
});

export default config; 4. to access env variables, use config object
