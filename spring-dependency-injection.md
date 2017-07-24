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
	3. **pros & cons for coupling**
  		* difficult to test
		* difficult to reuse
		* difficult to understand
		* 改一个崩一堆
	4. **DI的作用**
	
		_**Object are given their dependencies at creation time by some third party that coordinates each object in the system. Object aren't expected to create or obtain their dependencies**_

