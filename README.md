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





