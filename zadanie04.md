odpowiedz z localhost:5000/healts:

{"status":"ok"}

linia z docker logs:

172.18.0.1 - - [13/Nov/2026 13:38:30] "GET /health HTTP/1.1" 200 -


SONDY:

PS C:\Users\Student_PL\Desktop\Marek Giernacki\breach-checker-main> docker run --rm --network breach-net healthcheck-probe
backend: OK
PS C:\Users\Student_PL\Desktop\Marek Giernacki\breach-checker-main> docker run --rm healthcheck-probe
backend: UNREACHABLE
PS C:\Users\Student_PL\Desktop\Marek Giernacki\breach-checker-main> docker stop backend
backend
PS C:\Users\Student_PL\Desktop\Marek Giernacki\breach-checker-main> docker run --rm --network breach-net healthcheck-probe
backend: UNREACHABLE
PS C:\Users\Student_PL\Desktop\Marek Giernacki\breach-checker-main> docker start backend
backend


trwalosc danych:

PS C:\Users\Student_PL\Desktop\Marek Giernacki\breach-checker-main> docker run --rm -v breach-dane:/dane alpine sh -c "date >> /dane/historia.txt"
PS C:\Users\Student_PL\Desktop\Marek Giernacki\breach-checker-main> docker run --rm -v breach-dane:/dane alpine sh -c "date >> /dane/historia.txt; cat /dane/historia.txt"
Fri Nov 13 13:54:31 UTC 2026
Fri Nov 13 13:54:51 UTC 2026
PS C:\Users\Student_PL\Desktop\Marek Giernacki\breach-checker-main> docker volume ls
DRIVER    VOLUME NAME
local     breach-dane