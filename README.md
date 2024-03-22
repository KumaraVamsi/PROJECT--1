import java.util.Timer;
import java.util.TimerTask;

public class IrrigationSystem {
    private static final int MOISTURE_THRESHOLD = 500; // Adjust threshold as needed
    private static final int WATERING_DURATION = 5000; // Duration of watering in milliseconds

    private boolean isWatering = false;

    public void start() {
        Timer timer = new Timer();
        timer.schedule(new TimerTask() {
            @Override
            public void run() {
                int moistureLevel = readMoistureLevel();
                if (moistureLevel < MOISTURE_THRESHOLD && !isWatering) {
                    startWatering();
                }
            }
        }, 0, 1000); // Check moisture level every second
    }

    private int readMoistureLevel() {
        // Code to read soil moisture level from sensor
        return 450; // Placeholder value, replace with actual sensor reading
    }

    private void startWatering() {
        isWatering = true;
        System.out.println("Watering...");
        // Code to activate water pump
        // For demonstration purposes, simulate watering duration with a delay
        try {
            Thread.sleep(WATERING_DURATION);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        stopWatering();
    }

    private void stopWatering() {
        isWatering = false;
        System.out.println("Watering complete");
        // Code to deactivate water pump
    }

    public static void main(String[] args) {
        IrrigationSystem irrigationSystem = new IrrigationSystem();
        irrigationSystem.start();
    }
}
