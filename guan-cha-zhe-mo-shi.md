**1. 定义\(Observer Pattern /   Publish/Subscribe\)**
   1. 定义对象之间一种一对多的依赖关系，使得每一个对象的状态改变，则所有依赖于它的对象都会得到通知并且自动更新。
**2. 代码实例**
   1. Observer Interface:
      ```
      public interface Observer {
          public void update(String context);
      }
      ```

      

   2. Observable Interface:


       ```
      public interface Observable {
          public void addObserver(Observer observer);

          public void deleteObserver(Observer observer);

          public void notifyObserver(String context);

      }
       ```

   4. Observee Interface:

      ```
      public interface ISilva {
          public void haveBreakfast();

          public void plot();
      }
      ```

      Observee Class:

   5. ```
      public class Silva implements Observable, ISilva {
          private List<Observer> observerList;

          public Silva() {
              this.observerList = new ArrayList<>();
          }

          @Override
          public void addObserver(Observer observer) {
              this.observerList.add(observer);
          }

          @Override
          public void deleteObserver(Observer observer) {
              this.observerList.remove(observer);
          }

          @Override
          public void notifyObserver(String context) {
              for (Observer observer : observerList) {
                  observer.update(context);
              }
          }

          @Override
          public void haveBreakfast() {
              String context = "Silva is having breakfast";
              System.out.println("Silva: " + context);
              this.notifyObserver(context);
          }

          @Override
          public void plot() {
              String context = "Silva is plotting";
              System.out.println("Silva: " + context);
              this.notifyObserver(context);
          }
      }
      ```

      Observer Class 1:

   6. ```
      public class Bond implements Observer {

          @Override
          public void update(String context) {
              System.out.println("Bond:  Silva is doing something, begin to report..");
              this.reportToMadamM(context);
              System.out.println("Bond: Done reporting.\n");
          }

          private void reportToMadamM(String reportContext) {
              System.out.println("Bond: M, we observed that: -->" + reportContext);
          }
      }
      ```

      Observer Class 2:

   7. ```
      public class Band implements Observer {

          @Override
          public void update(String context) {
              System.out.println("Band:  Silva is doing something, begin to cry..");
              this.cry(context);
              System.out.println("Band: Done crying.\n");
          }

          private void cry(String reportContext) {
              System.out.println("Band: I'm crying because: -->" + reportContext);
          }
      }
      ```

      Observer Class 3:

   8. ```
      public class Bend implements Observer{

          @Override
          public void update(String context) {
              System.out.println("Bend:  Silva is doing something, begin to laugh..");
              this.laugh(context);
              System.out.println("Bend: Done laughing.\n");
          }

          private void laugh(String reportContext) {
              System.out.println("Bend: I'm laughing because: -->" + reportContext);
          }
      }
      ```

      Client:

   9. ```
      public class ObserverClient {
          public static void main(String[] args) {
              Observer bond = new Bond();
              Observer band = new Band();
              Observer bend = new Bend();

              Silva silva = new Silva();

              silva.addObserver(bond);
              silva.addObserver(bend);
              silva.addObserver(band);

              silva.haveBreakfast();
              silva.plot();
          }
      }
      ```



