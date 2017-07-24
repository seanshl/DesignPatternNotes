# Dependency Injection -- Core of Spring
* **简化Java开发**
	* **Spring Bean**: 不遵守EJB规范，可以是 _**任意pojo**_
	* **non-invasive**: 不需要你的class去extends/implements规定的其他类，非侵入式
* **Dependency Injection** :
	1. Application大多包括多个class. 一般来说每个对象需要负责保留一份与它协同工作的其他对象的reference/dependency. 这带来了很强的耦合. 
	2. **Example**
		```
		  public class DamselRescuingNight implements Knight {
			private RescueDamselQuest quest;

			public DamselRescuingKnight() {
				this.quest = new RescueDamselQuest();
			}

			public void embarkOnQuest() {
				quest.embark();
			}
		  }
  		```
		DamselRescuingKnight需要创建RescueDamselRequest, 使得二者耦合度很高。同时增加写测试代码的难度.
		DamselRescuingKnight只能创建Quest的一种Implementation, 由于使用了new的原因，它必须知道到底要创建那种具体的Quest.
	3. **pros & cons for coupling**
  		* difficult to test
		* difficult to reuse
		* difficult to understand
		* 改一个崩一堆
	4. **DI的作用**
	
		_**Object are given their dependencies at creation time by some third party that coordinates each object in the system. Object aren't expected to create or obtain their dependencies**_
	5. **Constructor Injection**
		```
		public class BraveKnight implements Knight {
			private Quest quest;
			public BraveKnight(Quest quest) {
				this.quest = quest;
			}
			public void embarkOnQuest() {
				quest.embark();
			}
		}
		```
		* BraveKnight并不创建自己的quest,而是**通过构造方法**直接传入变量. Quest本身也是一个Interface. BraveKnight**并不需要知道如何创建/创建哪个Quest.**
		
		* _**BraveKnight并不与Quest的任何Implementation耦合, 这是DI的最大好处，去耦合.**_
		* **If an object only knows about its dependencies by their interace (not by their implementation or how they're instantiated), then the dependency can be swapped out with a different implementation without the depending object know the difference**
	6. **Wiring**
		

