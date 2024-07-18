@echo off
REM Configuration
set "DB_USER=root"
set "DB_PASSWORD="
set "DB_NAME="
set "BACKUP_DIR=C:\Users\USERNAME\Desktop\Backup SQL"
set "MYSQLDUMP_PATH=C:\Program Files\MariaDB 11.4\bin\mysqldump.exe"
for /F "tokens=1-4 delims=/- " %%A in ('date /t') do (
    set "DATE=%%C%%A%%B"
)
for /F "tokens=1-2 delims=: " %%A in ('time /t') do (
    set "TIME=%%A%%B"
)
set "BACKUP_FILE=%BACKUP_DIR%\%DB_NAME%_backup_%DATE%_%TIME%.sql"
set "LOG_FILE=%BACKUP_DIR%\backup.log"
set "ERROR_LOG_FILE=%BACKUP_DIR%\backup_error.log"

REM Create backup directory if it does not exist
if not exist "%BACKUP_DIR%" (
    mkdir "%BACKUP_DIR%"
)

REM Perform backup using mysqldump
echo Starting backup for database: %DB_NAME% at %DATE% %TIME% >> "%LOG_FILE%"
"%MYSQLDUMP_PATH%" -u%DB_USER% -p%DB_PASSWORD% %DB_NAME% > "%BACKUP_FILE%" 2> "%ERROR_LOG_FILE%"

REM Check if the backup was successful
if %errorlevel%==0 (
    echo Backup successful: %BACKUP_FILE% >> "%LOG_FILE%"
    
    REM Optional: compress the backup file
    "C:\Program Files\7-Zip\7z.exe" a "%BACKUP_FILE%.7z" "%BACKUP_FILE%"
    del "%BACKUP_FILE%"
    echo Backup file compressed: %BACKUP_FILE%.7z >> "%LOG_FILE%"
) else (
    echo Backup failed for database: %DB_NAME% at %DATE% %TIME% >> "%LOG_FILE%"
    type "%ERROR_LOG_FILE%" >> "%LOG_FILE%"
    timeout /t 5
    exit /b 1
)

echo Backup completed at %DATE% %TIME% >> "%LOG_FILE%"
timeout /t 5
exit /b 0
