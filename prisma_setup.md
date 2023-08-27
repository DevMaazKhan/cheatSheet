install prisma
-- npm i prisma -D
-- npm i @prisma/client

initialize prisma
-- npx prisma init

For postgres Database write in schema.prisma file:
generator client {
provider = "prisma-client-js"
}

datasource db {
provider = "postgresql"
url = "postgresql://postgres:maazi@localhost:5432/learn"
}

paste these to top, for postgres, and than create your models

model User {
id Int @id @default(autoincrement())
email String @unique
name String
}

After making changes, when you want to replicate the changes into the DB, run
-- npx prisma migrate dev --name init

create file in util folder
touch src/util/db.ts

add this in db.ts
import { PrismaClient } from '@prisma/client';

const prisma = new PrismaClient();

export default prisma;
