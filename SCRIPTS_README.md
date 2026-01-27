# Spring Boot Management Scripts

This directory contains convenient scripts for managing the Spring Boot backend.

## Available Scripts

### 🔄 restart.sh
**Restart the Spring Boot backend**
```bash
./restart.sh
```
- Stops the existing Spring Boot process
- Starts a new instance
- Waits for the application to be ready
- Shows status and health check

### ▶️ start.sh
**Start the Spring Boot backend**
```bash
./start.sh
```
- Checks if already running
- Starts Spring Boot in background
- Logs output to `server.log`
- Verifies startup success

### ⏹️ stop.sh
**Stop the Spring Boot backend**
```bash
./stop.sh
```
- Gracefully stops Spring Boot
- Force kills if necessary
- Verifies process stopped

### 📊 status.sh
**Check Spring Boot status**
```bash
./status.sh
```
- Shows if running or stopped
- Displays PID and health status
- Shows memory/CPU usage
- Shows recent logs

### 📧 test_email.sh
**Send a test email**
```bash
./test_email.sh recipient@example.com "Subject" "Message"
```
- Tests email functionality
- Verifies SMTP configuration
- Shows delivery status

## Quick Reference

### Common Tasks

**Restart after code changes:**
```bash
./restart.sh
```

**Check if running:**
```bash
./status.sh
```

**View live logs:**
```bash
tail -f server.log
```

**Stop the server:**
```bash
./stop.sh
```

**Start the server:**
```bash
./start.sh
```

### Log Files

- **server.log** - Main application log
- All output from Spring Boot is logged here

### Port Information

- **Application Port:** 8080
- **Accessible at:** http://localhost:8080
- **Health Check:** http://localhost:8080/actuator/health

### Troubleshooting

**Server won't start:**
```bash
# Check logs
tail -50 server.log

# Check if port is in use
lsof -i :8080

# Force kill any existing process
pkill -9 -f spring-boot:run
```

**Email not working:**
```bash
# Send test email
./test_email.sh your-email@example.com

# Check email logs
tail -f server.log | grep -i email
```

**Application not responding:**
```bash
# Check status
./status.sh

# Restart
./restart.sh
```

## Environment

- **Java Version:** 17+
- **Spring Boot Version:** 3.x
- **Build Tool:** Maven
- **Email Server:** mail.visad.co.uk:465
- **Email From:** info@visad.co.uk

## Important Notes

1. **Background Process:** Spring Boot runs in the background via `nohup`
2. **Log Rotation:** Logs are appended to `server.log` (consider log rotation for production)
3. **Startup Time:** Application takes ~15-20 seconds to fully start
4. **Health Check:** Uses Spring Boot Actuator health endpoint

## Production Deployment

For production, consider using:
- **systemd service** for automatic restart
- **Log rotation** via logrotate
- **Monitoring** with health checks
- **Reverse proxy** via nginx (already configured)

## Git Integration

All scripts are version controlled. After making changes:
```bash
git add *.sh
git commit -m "Update management scripts"
git push
```

---

**Last Updated:** 2026-01-27
**Maintained by:** Development Team
