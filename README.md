# recursos-en-linea
 URLs de informacion de utilidad del lenguaje JAVA


https://www.oracle.com/technetwork/cn/community/developer-day/2-55-new-features-java-se-8-2202551-zhs.pdf

https://howtodoinjava.com/java-8-tutorial/

https://www.geeksforgeeks.org/lambda-expressions-java-8/

HTTP 2

https://developers.google.com/web/fundamentals/performance/http2?hl=es


DOCKER

https://courses.springframework.guru/p/introduction-to-docker?utm_source=sidebar




import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class MethodCallDiagram {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Ingrese el nombre del archivo de entrada: ");
        String inputFile = scanner.nextLine();

        Map<String, Map<String, Integer>> callGraph = parseCallGraph(inputFile);

        System.out.print("Ingrese el nombre del método (sin paréntesis): ");
        String methodName = scanner.nextLine();

        printCallDiagram(callGraph, methodName);

        System.out.println("Presione 'A' para buscar otro método o 'C' para salir.");
        String choice = scanner.nextLine();
        if (choice.equalsIgnoreCase("A")) {
            main(args);
        }
    }

    private static Map<String, Map<String, Integer>> parseCallGraph(String inputFile) {
        Map<String, Map<String, Integer>> callGraph = new HashMap<>();

        try (BufferedReader reader = new BufferedReader(new FileReader(inputFile))) {
            String line;
            while ((line = reader.readLine()) != null) {
                String[] parts = line.split(",");
                if (parts.length == 3) {
                    String caller = parts[0].trim();
                    String callee = parts[1].trim();
                    int callCount = Integer.parseInt(parts[2].trim());

                    if (!callGraph.containsKey(caller)) {
                        callGraph.put(caller, new HashMap<>());
                    }
                    callGraph.get(caller).put(callee, callCount);
                }
            }
        } catch (IOException e) {
            System.err.println("Error al leer el archivo: " + e.getMessage());
        }

        return callGraph;
    }

    private static void printCallDiagram(Map<String, Map<String, Integer>> callGraph, String methodName) {
        if (!callGraph.containsKey(methodName)) {
            System.out.println("No se encontró el método: " + methodName);
            return;
        }

        System.out.println("Diagrama de llamadas para el método: " + methodName);
        System.out.println("Clase,Método,Recuento de llamadas");

        Map<String, Integer> calledMethods = callGraph.get(methodName);
        for (Map.Entry<String, Integer> entry : calledMethods.entrySet()) {
            String callee = entry.getKey();
            int callCount = entry.getValue();
            System.out.println(methodName + "," + callee + "," + callCount);
        }
    }
}






import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class MethodCallDiagram {
    public static void main(String[] args) {
        // Crear un objeto Scanner para leer la entrada del usuario
        Scanner scanner = new Scanner(System.in);

        // Solicitar al usuario el nombre del archivo de entrada
        System.out.print("Ingrese el nombre del archivo de entrada: ");
        String inputFile = scanner.nextLine();

        // Analizar el archivo de entrada y crear el gráfico de llamadas
        Map<String, Map<String, Integer>> callGraph = parseCallGraph(inputFile);

        // Solicitar al usuario el nombre del método para el que quiere generar el diagrama
        System.out.print("Ingrese el nombre del método (sin paréntesis): ");
        String methodName = scanner.nextLine();

        // Imprimir el diagrama de llamadas para el método especificado
        printCallDiagram(callGraph, methodName);

        // Dar al usuario la opción de buscar otro método o salir
        System.out.println("Presione 'A' para buscar otro método o 'C' para salir.");
        String choice = scanner.nextLine();
        if (choice.equalsIgnoreCase("A")) {
            main(args); // Llamar recursivamente al método main para permitir una nueva búsqueda
        }
    }

    private static Map<String, Map<String, Integer>> parseCallGraph(String inputFile) {
        // Crear un mapa principal para almacenar el gráfico de llamadas
        Map<String, Map<String, Integer>> callGraph = new HashMap<>();

        try (BufferedReader reader = new BufferedReader(new FileReader(inputFile))) {
            String line;
            while ((line = reader.readLine()) != null) {
                // Cada línea del archivo debe tener el formato: "caller,callee,callCount"
                String[] parts = line.split(",");
                if (parts.length == 3) {
                    String caller = parts[0].trim(); // Método que llama
                    String callee = parts[1].trim(); // Método que es llamado
                    int callCount = Integer.parseInt(parts[2].trim()); // Número de veces que se llama

                    // Si el método que llama no existe en el mapa, crear una nueva entrada
                    if (!callGraph.containsKey(caller)) {
                        callGraph.put(caller, new HashMap<>());
                    }
                    // Agregar la información de llamada al mapa
                    callGraph.get(caller).put(callee, callCount);
                }
            }
        } catch (IOException e) {
            System.err.println("Error al leer el archivo: " + e.getMessage());
        }

        return callGraph;
    }

    private static void printCallDiagram(Map<String, Map<String, Integer>> callGraph, String methodName) {
        // Verificar si el método especificado existe en el gráfico de llamadas
        if (!callGraph.containsKey(methodName)) {
            System.out.println("No se encontró el método: " + methodName);
            return;
        }

        System.out.println("Diagrama de llamadas para el método: " + methodName);
        System.out.println("Clase,Método,Recuento de llamadas");

        // Obtener los métodos llamados por el método especificado
        Map<String, Integer> calledMethods = callGraph.get(methodName);
        for (Map.Entry<String, Integer> entry : calledMethods.entrySet()) {
            String callee = entry.getKey(); // Método llamado
            int callCount = entry.getValue(); // Número de veces que se llamó
            System.out.println(methodName + "," + callee + "," + callCount);
        }
    }
}





@echo off

REM Set was_home environment variable
setx was_home "C:\Users" /m

REM Set ant_home environment variable 
setx ant_home "C:\Users" /m

echo Environment variables set:
echo was_home = %was_home%
echo ant_home = %ant_home%



/////


@echo off

# Set was_home and ant_home environment variables
setx was_home "C:\Users" /m
setx ant_home "C:\Users" /m

echo Environment variables set:
echo was_home = %was_home%
echo ant_home = %ant_home%





@echo off

REM Set was_home and ant_home for the current session
set was_home="C:\Users"
set ant_home="C:\Users"

REM Set was_home and ant_home permanently
setx was_home "C:\Users" /m
setx ant_home "C:\Users" /m

REM Display environment variables
echo Environment variables set:
echo was_home = %was_home%
echo ant_home = %ant_home%



//////



1. Agrega las Dependencias
Asegúrate de agregar las siguientes dependencias en tu archivo pom.xml:

XML
<dependency>
    <groupId>com.ibm.mq</groupId>
    <artifactId>com.ibm.mq.allclient</artifactId>
    <version>9.2.0.0</version>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-activemq</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jms</artifactId>
</dependency>
2. Configura las Propiedades
Configura las propiedades de conexión en el archivo application.properties:

Code
ibm.mq.queueManager=QUEUE_MANAGER_NAME
ibm.mq.channel=CHANNEL_NAME
ibm.mq.connName=HOSTNAME(PORT)
ibm.mq.user=USERNAME
ibm.mq.password=PASSWORD
spring.jms.template.default-destination=QUEUE_NAME
3. Configura el JmsTemplate
Crea una clase de configuración para definir el JmsTemplate:

Java
import com.ibm.mq.jms.MQConnectionFactory;
import com.ibm.msg.client.wmq.WMQConstants;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.jms.annotation.EnableJms;
import org.springframework.jms.core.JmsTemplate;

import javax.jms.JMSException;

@Configuration
@EnableJms
public class JmsConfig {

    @Bean
    public MQConnectionFactory mqConnectionFactory() throws JMSException {
        MQConnectionFactory factory = new MQConnectionFactory();
        factory.setHostName("HOSTNAME");
        factory.setPort(1414);
        factory.setQueueManager("QUEUE_MANAGER_NAME");
        factory.setChannel("CHANNEL_NAME");
        factory.setTransportType(WMQConstants.WMQ_CM_CLIENT);
        factory.setStringProperty(WMQConstants.USERID, "USERNAME");
        factory.setStringProperty(WMQConstants.PASSWORD, "PASSWORD");
        return factory;
    }

    @Bean
    public JmsTemplate jmsTemplate(MQConnectionFactory mqConnectionFactory) {
        return new JmsTemplate(mqConnectionFactory);
    }
}
4. Leer y Escribir en la Cola
Utiliza JmsTemplate para leer y escribir mensajes en la cola.

Clase para enviar mensajes:

Java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jms.core.JmsTemplate;
import org.springframework.stereotype.Component;

@Component
public class MessageSender {

    @Autowired
    private JmsTemplate jmsTemplate;

    public void sendMessage(String message) {
        jmsTemplate.convertAndSend("QUEUE_NAME", message);
    }
}
Clase para recibir mensajes:

Java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jms.core.JmsTemplate;
import org.springframework.stereotype.Component;

@Component
public class MessageReceiver {

    @Autowired
    private JmsTemplate jmsTemplate;

    public String receiveMessage() {
        return (String) jmsTemplate.receiveAndConvert("QUEUE_NAME");
    }
}
5. Clase de Prueba
Escribe una clase de prueba para verificar la funcionalidad de lectura y escritura.

Java
import static org.junit.jupiter.api.Assertions.assertEquals;
import static org.mockito.Mockito.*;

import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoExtension;
import org.springframework.jms.core.JmsTemplate;

@ExtendWith(MockitoExtension.class)
public class JmsServiceTest {

    @Mock
    private JmsTemplate jmsTemplate;

    @InjectMocks
    private MessageSender messageSender;

    @InjectMocks
    private MessageReceiver messageReceiver;

    private final String queueName = "QUEUE_NAME";
    private final String message = "Test Message";

    @BeforeEach
    public void setup() {
        messageSender = new MessageSender(jmsTemplate);
        messageReceiver = new MessageReceiver(jmsTemplate);
    }

    @Test
    public void testSendMessage() {
        doNothing().when(jmsTemplate).convertAndSend(queueName, message);
        messageSender.sendMessage(message);
        verify(jmsTemplate, times(1)).convertAndSend(queueName, message);
    }

    @Test
    public void testReceiveMessage() {
        when(jmsTemplate.receiveAndConvert(queueName)).thenReturn(message);
        String receivedMessage = messageReceiver.receiveMessage();
        assertEquals(message, receivedMessage);
    }
}
Este ejemplo cubre la configuración básica y las pruebas para leer y escribir en una cola de IBM MQ utilizando JmsTemplate en un proyecto Spring Boot 3.x. Asegúrate de ajustar los valores y nombres según tu configuración específica.

