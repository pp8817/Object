# ch15 디자인 패턴과 프레임워크

sw 설계에서 반복적으로 발생하는 문제에 대해 반복적으로 적용할 수 있는 해결 방법을 ‘디자인 패턴’이라고 한다.

목적 : 설계를 재사용하는 것.

다양한 변경을 다루기 위해 반복적으로 재사용할 수 있는 설계의 묶음이다.
변경의 방향과 주기를 이해하는 것만으로도 필요한 역할과 책임, 역할들의 협력 방식을 순간적으로 떠올릴 수 있게 된다.

**디자인 패턴**이 설계를 재사용하기 위한 것이며, **프레임워크**는 설계와 코드를 함께 재사용하기 위한 것이다.

app의 아키텍처를 구현 코드의 형태로 제공한다.

14챕터에선 일관성 있는 협력과 관련이 있다.

디자인 패턴은 특정한 변경을 일관성있게 다룰 수 있도록 ‘협력 템플릿을 제공’한다.

디자인 패턴이 협력을 일관성 있게 만들기 위해 재사용할 수 있는 설계의 묶음이라면, 프레임워크는 일관성 있는 협력을 제공하는 확장 가능한 코드라고 할 수 있다. 결론적으로 디자인 패턴과 프레임워크 모두 협력을 일관성 있게 만들기 위한 방법이다.

---

# 디자인 패턴과 설계 재사용

## 소프트웨어 패턴

패턴의 정의보다는 패턴이라는 용어 자체가 풍기는 미묘한 뉘앙스를 이해하는 것이 중요하다.

몇 가지 핵심적인 특징

1. 패턴은 반복적으로 발생하는 문제와 해법의 쌍으로 정의된다.
2. 패턴을 사용함으로써 이미 알려진 문제와 이에 대한 해법을 문서로 정리할 수 있으며, 이 지식을 다른 사람과 의사소통 할 수 있다.
3. 패턴은 추상적인 원칙과 실제 코드 작성 사이의 간극을 메워주며 실질적인 코드 작성을 돕는다
4. 패턴의 요점은 패턴이 실무에서 탄생했다는 점이다

> 패턴은 개발자들이 다른 컨텍스트에서도 유용할 것이라고 생각하는 어떤 것이다
> 

패턴은 한 컨텍스트에서의 ‘아이디어’다.

패턴으로 인정하기 위한 조건으로 ‘3의 규칙’을 언급한다.

"3의 규칙"(Rule of Three)은 소프트웨어 엔지니어링과 특히 소프트웨어 디자인 패턴에서 언급되는 개념입니다. 이 규칙은 어떤 솔루션이나 패턴이 일반적으로 인정받기 위해서는 적어도 세 번 이상 다양한 상황에서 성공적으로 적용되어야 한다는 원칙을 말합니다. 
"3의 규칙"은 디자인 패턴이나 프로그래밍 관행이 널리 인정받기 위한 비공식적인 기준으로 사용됩니다. 
이 규칙의 핵심 아이디어는 단순히 이론적이거나 한 번만 사용된 아이디어가 아니라, 실제로 다양한 문제를 해결하는 데에 반복적으로 유용함이 입증된 솔루션을 패턴으로 인정하자는 것입니다.

### **3의 규칙이 필요한 이유**

1. **재사용성의 검증:** 하나의 상황에서만 유용한 솔루션이 아니라, 다양한 문제 상황에서 재사용할 수 있는지 확인합니다. 이는 디자인 패턴의 재사용성과 범용성을 검증하는 과정입니다.
2. **유연성과 일반성:** 세 번 이상 다양한 상황에서의 성공적인 적용은, 해당 솔루션이 특정 문제에만 국한되지 않고, 다양한 문제 상황에 유연하게 적용될 수 있는 일반적인 해결책임을 보여줍니다.
3. **공동체의 합의:** 소프트웨어 개발 커뮤니티 내에서 널리 사용되고 인정받는 방법론이나 패턴은, 그만큼 검증된 솔루션이라는 의미를 내포합니다. "3의 규칙"은 이러한 커뮤니티 내 합의에 기반한 검증 절차의 일부로 볼 수 있습니다.

### **적용 예시**

- **디자인 패턴:** 객체 지향 프로그래밍에서 널리 알려진 디자인 패턴들(예: 싱글턴, 팩토리, 옵저버 패턴 등)은 다양한 프로젝트와 상황에서 반복적으로 사용되어 그 유용성이 입증되었습니다.
- **소프트웨어 원칙:** SOLID 원칙, DRY(Don't Repeat Yourself), KISS(Keep It Simple, Stupid)와 같은 소프트웨어 개발 원칙들 역시 다양한 상황에서의 적용을 통해 그 가치가 검증되었습니다.

"3의 규칙"은 소프트웨어 개발에 있어서 경험적인 지식과 베스트 프랙티스의 중요성을 강조합니다.
이는 개발자들이 보다 나은 아키텍처와 코드 설계를 위해 검증된 패턴과 원칙들을 참고하고 적용하도록 독려하는 데 목적이 있다.

패턴이 지닌 가장 큰 가치는 경험을 통해 축적된 실무 지식을 효과적으로 요약하고 전달할 수 있다는 점이다.

즉, 패턴은 경험의 산물이다.

가장 중요한 요소는 패턴의 ‘이름’이다.
잘 알려진 이름을 사용함으로써 “인터페이스를 하나 추가하고 이 인터페이스를 구체화하는 클래스를 만든 후 객체의 생성자나 setter 메서드에 할당해서 런타임 시에 알고리즘을 바꿀 수 있게 하자”는 장황한 대화가 STRATEGY 패턴을 적용하자는 단순한 대화로 끝나게 된다.

### **스트래티지 패턴의 구성 요소**

1. **Context (문맥):** 사용자가 사용할 수 있는 인터페이스를 제공합니다. Context는 Strategy를 사용하여 특정 작업을 실행합니다.
2. **Strategy Interface (전략 인터페이스):** 모든 Concrete Strategies가 구현해야 하는 일반적인 인터페이스입니다. 이 인터페이스는 각 Concrete Strategy가 구현할 알고리즘에 대한 메서드를 선언합니다.
3. **Concrete Strategies (구체적인 전략들):** Strategy 인터페이스를 구현하는 클래스들입니다. 이 클래스들은 인터페이스에 선언된 알고리즘을 구체적으로 구현합니다.

### **스트래티지 패턴의 예**

고객에게 할인을 제공하는 다양한 전략을 구현하는 예시를 들 수 있습니다. 예를 들어, **`NoDiscount`**, **`SeasonalDiscount`**, **`LoyaltyDiscount`** 등 다양한 할인 전략이 있을 수 있으며, 각 전략은 **`DiscountStrategy`** 인터페이스를 구현합니다. **`BillingSystem`** 클래스(문맥)는 **`DiscountStrategy`**를 사용하여 최종 가격을 계산합니다. 이 때, **`BillingSystem`**은 실행 시점에 어떤 할인 전략을 사용할지 결정할 수 있습니다.

```java
interface DiscountStrategy {
    double applyDiscount(double price);
}

class NoDiscount implements DiscountStrategy {
    public double applyDiscount(double price) {
        return price; // 할인 없음
    }
}

class SeasonalDiscount implements DiscountStrategy {
    public double applyDiscount(double price) {
        return price * 0.9; // 10% 할인
    }
}

class LoyaltyDiscount implements DiscountStrategy {
    public double applyDiscount(double price) {
        return price * 0.8; // 20% 할인
    }
}

class BillingSystem {
    private DiscountStrategy discountStrategy;

    public BillingSystem(DiscountStrategy discountStrategy) {
        this.discountStrategy = discountStrategy;
    }

    public double calculatePrice(double price) {
        return discountStrategy.applyDiscount(price);
    }

    // 할인 전략을 변경할 수 있는 메서드
    public void setDiscountStrategy(DiscountStrategy discountStrategy) {
        this.discountStrategy = discountStrategy;
    }
}

public class StrategyPatternExample {
    public static void main(String[] args) {
        BillingSystem system = new BillingSystem(new NoDiscount());
        System.out.println(system.calculatePrice(100)); // 100

        system.setDiscountStrategy(new SeasonalDiscount());
        System.out.println(system.calculatePrice(100)); // 90

        system.setDiscountStrategy(new LoyaltyDiscount());
        System.out.println(system.calculatePrice(100)); // 80
    }
}
```

이 예에서 **`BillingSystem`**은 실행 시점에 할인 전략을 바꿀 수 있으므로, 같은 **`calculatePrice`** 메서드를 사용하면서도 다양한 할인 정책을 적용할 수 있습니다. 이처럼 스트래티지 패턴은 알고리즘의 교체를 용이하게 하여 코드의 유연성과 확장성을 크게 향상시킵니다.

이처럼 마틴 파울러가 언급한 것처럼 패턴의 범위가 한정되는 것은 아니다.
반복적인 규칙을 발견할 수 있는 모든 영역이 패턴의 대상이 될 수 있다.

패턴은 홀로 존재하지 않는다.
특정 패턴 내에 포함된 컴포넌트 간의 관게는 더 작은 패턴에 의해 서술될 수 있으며, 패턴들을 포함하는 더 큰 패턴 내에 통합될 수 있다.

---

## 패턴 분류

패턴의 범위나 적용 단계에 따라 1. 아키텍처 패턴 , 2. 분석 패턴, 3. 디자인 패턴 , 4. 이디엄의 4가지로 분류하는 것이다.

디자인 패턴의 꽃은 전략 패턴이다.

**아키텍처 패턴**

디자인 패턴의 상위에는 소프트웨어의 전체적인 구조를 결정하기 위해 사용할 수 있다.

미리 정의된 서브시스템들을 제공하고, 각 서브시스템들의 책임을 정의하며, 서브시스템들 사이의 관계를 조직화하는 규칙과 가이드라인을 포함한다.

디자인 패턴의 하위에는 이디엄이 위치한다.

자바의 가비지 컬렉션 메커니즘을 가진 자바에선 유용하지 않다.

(아키텍처 패턴, 디자인 패턴, 이디엄) 주로 기술적인 문제를 해결하는 데 초점을 맞춤,
**분석 패턴**은 도메인 내의 개념적인 문제를 해결하는 데 초점.

## 패턴과 책임-주도 설게

패턴은 공통으로 사용할 수 있는 역할, 책임, 협력의 템플릿

STRATEGY패턴 : 다양한 알고리즘을 동적으로 교체할 수 있는 역할과 책임의 집합을 제공

BRIDGE패턴 : 추상화의 조합으로 인한 클래스의 폭발적인 증가 문제를 해결하기 위해 역할과 추상화와 구현의 두 개의 커다란 집합으로 분해함으로써 설계를 확장 가능하게 한다.

OBSERVER패턴 : 유연한 통지 메커니즘을 구축하기 위해 객체 간의 결합도를 낮출 수 있는 역할과 책임의 집합을 제공한다.

중요한 것은 패턴을 따르면 특정한 상황에 적용할 수 있는 설계를 빠르게 떠올릴 수 있다는 사실이다.

***패턴의 구성요소는 클래스가 아니라 ‘역할’이다.***

COMPOSITE 패턴을 확인해보자.  (517p)

역할이라는 사실은 패턴 템플릿을 구현할 수 있는 다양한 방법이 존재한다는 사실을 암시한다.

중복 설계의 기본 구조는 COMPOSITE패턴을 따른다.

다시 말하지만, 
디자인 패턴의 구성요소가 클래스와 메서드가 아니라 역할과 책임이라는 사실을 이해하는 것이 가장 중요하다.

역할, 책임, 협력의 관점에서 유사성을 공유한다는 것이지 특정한 구현 방식을 강제하는 것은 아니라는 점을 이해하는 것 역시 중요하다.

## 캡슐화와 디자인 패턴

결합도를 낮게 유지할 수 있게 된다면, 런타임에 알고리즘을 변경할 수 있게 된다.

변경을 캡슐화하는 방법이 합성만 있는 것은 아니다.
상속을 이용할 수도 있다.

변경하지 않는 부분은 부모 클래스로, 변하는 부분은 자식 클래스로 분리함으로써 변경을 캡슐화 한다.

추상 클래스나 인터페이스를 사용해 변경을 캡슐화하는 합성과 달리 상속을 사용할 경우에는 추상메서드를 이용해 변경을 캡슐화해야 한다. (서브클래스의 변경을 캡슐화하기 위해 사용되는 추상 메서드가 있다)

TEMPLATE METHOD 패턴은 부모 클래스가 알고리즘의 기본 구조를 정의하고 구체적인 단계는 자식 클래스에서 정의하게 함으로써 변경을 캡슐화할 수 있는 디자인 패턴이다.

합성보다는 결합도가 높은 상속을 사용했기 때문에 런타임에 객체의 알고리즘을 변경하는 것은 불가능하다.
하지만, 알고리즘 교체와 같은 요구사항이 없다면 상대적으로 STRATEGY 패턴보다 복잡도를 낮출 수 있다는 면에서는 장점이다.

DECORATOR 패턴 : 객체의 행동을 동적으로 추가할 수 있게 해주는 패턴

대부분의 디자인 패턴의 목적은 특정한 변경을 캡슐화함으로써 유연하고 일관성 있는 협력을 설계할 수 있는 경험을 공유하는 거싱다.

**디자인 패턴에서 가장 중요한 것은 디자인 패턴의 구현 방법이나 구조가 아니다.
어떤 디자인 패턴이 어떤 변경을 캡슐화하는지를 이해하는 것이 중요하다. 
그리고 각 디자인 패턴이 변경을 캡슐화하기 위해 어떤 방법을 사용하는지를 이해하는 것이 더 중요하다.**

---

## 패턴은 출발점이다.

패턴은 출발점이지 목적지가 아니다.

특정한 설계 이슈를 해결하기 위해 적절한 디자인 패턴을 이용해 설계를 시작한다.

그러나 패턴은 설계의 목표가 돼서는 안 된다.
패턴은 단지 목표로 하는 설계에 이룰 수 있는 방향을 제시하는 나침반에 불과하다.

목적에 맞게 패턴을 수정하라.

> 패턴은 틀을 제공할 뿐. 나에게 맞도록 수정하라고 있는 틀이다.
즉, 패턴은 “도화지”와 같다고 생각한다. 
어느 “물감”을 쓰느냐에 따라 그림의 분위기를 바꾸기 때문이다.
다만, 큰 틀은 “도화지"에서 출발했다는 것이다.
도구도 “물감”에서 각 색상을 선택해 그린다는 것이다.
> 

패턴을 상요하면서 부딪히게 되는 대부분의 문제는 패턴을 맹목적으로 사용할 때 발생한다.

패턴을 적용하는 컨텍스트의 적절성은 무시한 채 패턴의 구조에만 초점을 맞추는 것이다.

> 망치를 들면 모든 것이 못으로 보인다는 격언처럼 패턴을 익힌 후에는 모든 설계 문제를 패턴으로 해결하려고 시도하기 쉽다. 조슈아 케리에브스키는 이를 ‘패턴 만능주의'라고 부른다. 유의하자.
> 

### GoF 디자인 패턴

전문가는 다양한 실무 경험을 통해 어떤 컨텍스트에서 어떤 패턴을 적용해야 하는지, 그리고 이보다 더 중요한 것은 어떤 패턴을 적용해서는 안 되는지에 대한 감각을 익히고 있다는 점이다.

아무리 사소한 설계라도 패턴을 적용해보려고 시도한다.

그러나 명확한 트레이드오프 없이 패턴을 남용하면 설계가 불필요하게 복잡해지게 된다.

타당한 이유 없이 패턴을 적용하면 패턴에 익숙한 사람들의 경우에는 설계의 의도를 이해하지 못하게 되고, 패턴을 알지 못하는 사람들은 불필요하게 복잡한 설계를 따라가느라 시간을 낭비하게 된다.

패턴은 복잡성의 가치가 단순성을 넘어설 떄만 정당화 돼야 한다.
→ 이게 무슨 말이지 ???

→ 여기서 언급하는 "단순성"은 소프트웨어 설계와 개발에서 추구하는 중요한 원칙 중 하나입니다. 
단순성은 복잡성을 최소화하고, 코드의 가독성과 이해도를 높이며, 유지보수를 용이하게 하는 설계의 특성을 말합니다. 소프트웨어에서 단순성을 추구하는 것은 다음과 같은 이유에서 중요합니다.

1. **가독성과 이해도 향상:** 단순한 코드와 설계는 다른 개발자들이 코드를 더 쉽게 이해하고, 프로젝트에 기여하기 시작하는 데 걸리는 시간을 단축시킵니다. 코드가 명확하고 직관적일수록, 그 의도와 작동 원리를 파악하기가 더 쉽습니다.
2. **유지보수의 용이성:** 단순한 설계는 변경 사항을 적용하거나 버그를 수정하는 과정을 단순화합니다. 복잡성이 낮을수록 특정 부분을 수정할 때 발생할 수 있는 부작용을 예측하고 관리하기가 더 쉽습니다.
3. **오류의 감소:** 복잡한 코드와 설계는 오류가 발생하기 쉬운 환경을 조성합니다. 반면, 단순성은 오류가 발생할 여지를 줄여주고, 발생한 오류를 더 빨리 발견하고 수정할 수 있게 합니다.
4. **확장성과 재사용성:** 단순하고 깔끔한 코드는 재사용하기 쉽습니다. 또한, 시스템의 확장성이 높아집니다. 새로운 기능을 추가하거나 기존 기능을 확장할 때 기존의 단순한 구조를 기반으로 작업하기가 더 쉬워집니다.

단순성을 추구하는 것은 "더 적은 것이 더 많은 것이다(Less is More)"와 같은 원칙을 따르는 것과 유사합니다. 이는 소프트웨어 설계에서 불필요한 복잡성을 피하고, 설계와 코드를 가능한 한 단순하고 명확하게 유지하는 것을 목표로 합니다. 따라서, 설계나 개발 과정에서 복잡성을 추가하기 전에 그로 인해 얻는 가치가 단순성을 희생시키는 것을 정당화하는지 신중하게 고려해야 합니다.

---

# 프레임워크와 코드 재사용

### 코드 재사용 대 설계 재사용

재사용 관점에서 설계 재사용보다 더 좋은 방법은 코드 재사용이다.

가장 이상적인 형태의 재사용 방법 : 설계 재사용과 코드 재사용을 적절한 수준으로 조합하는 것

설계를 재사용하면서도 유사한 코드를 반복적으로 구현하는 문제를 피할 수 있는 방법은 없을까 ?

⇒ “프레임 워크”가 정답이다.

프레임워크란, 애플리케이션의 골격이다. 

### 상위 정책과 하위 정책으로 패키지 분리하기

추상 클래스와 인터페이스가 일관성 있는 협력을 만드는 핵심 재료.

협력을 일관성 있고 유연하게 만들기 위해서는 추상화를 이용해 변경을 캡슐화해야 한다.
그리고 협력을 구현하는 코드 안의 의존성은 가급적이면 추상 클래스나 인터페이스와 같은 추상화를 향하도록 작성해야 한다. 

추상화에 해당하는 부분을 짙은 색으로 표시한다.

상위 정책이 세부 사항에 비해 재사용될 가능성이 높다.

요점은 상위 정책이 세부 사항보다 더 다양한 상황에서 재사용될 수 있어야 한다는 것이다.
하지만 상위 정책이 세부 사항에 의존하게 되면 상위 정책이 필요한 모든 경우에 세부 사항도 항상 함께 존재해야 하기 때문에 상위 정책의 재사용성이 낮아진다. 이 문제를 해결할 수 있는 가장 좋은 방법은 의존성 역전 원칙에 맞게 상위 정책과 세부 사항 모두 추상화에 의존하게 만드는 것이다.

***변하는 것과 변하지 않는 것을 서로 분리해야 한다.***

## **제어 역전 원칙**

의존성 역전 원리는 전통적인 설계 방법과 객체지향을 구분하는 가장 핵심적인 원리다.

시스템이 진화하는 방향에는 항상 의존성 역전 원리를 따르는 설계가 존재해야 한다.

의존성 역전 원리가 적절하게 지켜지지 않고 있다면 그곳에는 변경을 적절하게 수용할 수 없는 하향식의 절차적인 코드가 존재할 수 밖에 없다.

**로버튼 마틴은 훌륭한 객체지향 설계는 의존성이 역전된 설계라는 점을 강조한다.**

좋은 객체지향 설계의 증명이 의존성의 역전이다.

프로그램의 의존성이 역전돼 있다면, 이것은 객체지향 설계를 갖는 것이다.

다시 말하면,

의존성 역전 원칙(DIP)은 소프트웨어 설계 원칙 중 하나로, 고수준 모듈이 저수준 모듈에 의존하지 않도록 하고, 
둘 다 추상화에 의존하도록 만드는 것입니다. 이 원칙의 핵심은 "의존성을 역전시키는" 것으로, 일반적으로 발생하는 상황은 고수준 모듈(복잡한 로직을 처리하는 클래스)이 저수준 모듈(데이터를 저장하거나 간단한 작업을 수행하는 클래스)에 직접 의존하는 것입니다. 의존성 역전 원칙을 적용하면, 이러한 의존성 구조를 뒤집어 추상화를 통해 두 모듈 간의 직접적인 의존성을 제거합니다.

이 원칙은 다음 두 가지 주요 지침으로 요약할 수 있습니다.

1. 고수준 모듈은 저수준 모듈의 구현에 의존해서는 안 됩니다. 둘 다 추상화에 의존해야 합니다.
2. 추상화는 세부 사항에 의존해서는 안 됩니다. 세부 사항이 추상화에 의존해야 합니다.

그렇다면, 궁금해 해야할 것압니다. 프로그램의 의존성이 역전돼 있는 코드란 무엇일까? 자바 코드로는 ?

의존성 역전 원칙을 적용한 간단한 자바 코드 예시를 살펴보겠습니다. 이 예시에서는 데이터를 처리하는 고수준 모듈 **`DataProcessor`**와 데이터를 저장하는 저수준 모듈 **`Database`**를 가정해 봅시다. 
**`Database`**는 **`DataStorage`** 인터페이스를 구현합니다.

```java
// 추상화 (인터페이스)
interface DataStorage {
    void saveData(String data);
}

// 저수준 모듈
class Database implements DataStorage {
    @Override
    public void saveData(String data) {
        System.out.println("Saving data to a database: " + data);
    }
}

// 고수준 모듈
class DataProcessor {
    private DataStorage dataStorage;

    // 의존성을 생성자를 통해 주입 (생성자 주입)
    public DataProcessor(DataStorage dataStorage) {
        this.dataStorage = dataStorage;
    }

    public void processData(String data) {
        System.out.println("Processing data: " + data);
        dataStorage.saveData(data);
    }
}

public class Main {
    public static void main(String[] args) {
        DataStorage database = new Database();
        DataProcessor processor = new DataProcessor(database);
        processor.processData("Some data");
    }
}
```

이 코드에서 **`DataProcessor`** 클래스(고수준 모듈)는 **`Database`** 클래스(저수준 모듈)에 직접 의존하지 않습니다. 대신, 둘 다 **`DataStorage`** 인터페이스(추상화)에 의존합니다. 이를 통해 고수준 모듈과 저수준 모듈 사이의 의존성이 역전됩니다. **`DataProcessor`**는 데이터 저장 방법의 세부 사항을 알 필요 없이 데이터를 처리할 수 있으며, **`Database`** 클래스를 다른 저장 메커니즘으로 교체하는 것이 용이해집니다. 이러한 방식으로 의존성 역전 원칙을 적용하면 시스템의 결합도를 낮추고 유연성 및 확장성을 향상시킬 수 있습니다.

의존성 역전은 의존성의 방향뿐만 아니라 제어 흐름의 주체 역시 역전시킨다,.

즉, 의존성을 역전시키면 제어 흐름의 주체 역시 역전된다는 말입니다.
이를 제**어 역전 원리** 또는 **할리우드 원리** 라고 합니다.

프레임 워크에서는 일반적인 해결책만 제공하고 애플리케이션에 따라 달라질 수 있는 특정한 동작은 비워둔다.
그리고 이렇게 완성되지 않는 채로 남겨진 동작을 훅이라고 부릅니다.
훅의 구현 방식은 애플리케이션의 컨텍스트에 따라 달라집니다.
혹은 프레임워크 코드에서 호출하는 프레임워크의 특정 부분입니다.

여기서 협력을 제어하는 것은 프레임워크라는 것에 주목하자.

제어가 우리에게서 프레임워크로 넘어가 버린 것이다. 즉, 제어가 역전된 것이다. 우리의 코드는 수동적인 존재다.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/075997f4-35b2-4955-b621-060d6a108880/5feb4c06-b937-470b-beb5-4cd133b38d2a/Untitled.heic)

### **제어 흐름의 불안함과 그 이해**

프레임워크를 처음 사용하는 개발자에게 IoC는 불안감을 줄 수 있습니다. 이는 개발자가 프로그램의 전체적인 제어 흐름을 직접 관리하지 않고, 어떤 코드가 언제 실행될지를 프레임워크에 의존하기 때문입니다. 프로그램의 실행 흐름이 개발자의 손을 떠나 프레임워크 내부로 "스멀스멀" 넘어가는 것처럼 느껴질 수 있습니다.

하지만, 이러한 제어의 역전은 프레임워크의 핵심적인 장점이기도 합니다. 이를 통해 코드의 재사용성이 높아지고, 애플리케이션 개발에 있어 일관된 구조를 제공받을 수 있으며, 복잡한 문제를 프레임워크가 추상화하여 간소화시켜 줍니다.

### **스프링 코드 예시**

아래는 Java Spring Framework에서 의존성 주입을 사용하는 간단한 예시입니다. Spring은 IoC 컨테이너를 제공하여, 개발자가 직접 객체를 생성하고 관리하는 대신 Spring 컨테이너가 객체의 생성과 생명주기를 관리합니다.

```java
@Component
public class MyService {
    private final MyRepository repository;

    @Autowired
    public MyService(MyRepository repository) {
        this.repository = repository;
    }

    public void doSomething() {
        // 여기서 비즈니스 로직을 수행합니다.
    }
}

@Component
public class MyRepository {
    public void saveData() {
        // 데이터 저장 로직
    }
}

@SpringBootApplication
public class MyApplication {
    public static void main(String[] args) {
        ApplicationContext ctx = SpringApplication.run(MyApplication.class, args);
        MyService myService = ctx.getBean(MyService.class);
        myService.doSomething();
    }
}

```

위 예시에서 **`@Autowired`** 어노테이션을 사용한 의존성 주입은 Spring Framework가 **`MyService`** 객체를 생성할 때, **`MyRepository`** 객체를 자동으로 주입해 주는 IoC의 한 예입니다. 개발자는 **`MyService`**와 **`MyRepository`**의 구체적인 생성과 연결 과정을 신경 쓸 필요 없이, 비즈니스 로직의 구현에 집중할 수 있습니다. 이처럼 제어의 역전은 프레임워크가 제공하는 강력한 도구이며, 코드 재사용성과 구조적인 일관성을 증진시키는 데 큰 도움을 줍니다.
