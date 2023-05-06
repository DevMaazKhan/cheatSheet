install prisma
-- npm i prisma -D

initialize prisma
-- npx prisma --init

After making changes, when you want to replicate the changes into the DB, run
-- npx prisma migrate dev --name init
