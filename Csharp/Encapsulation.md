#OOP #OOPSConcepts

Encapsulation is the process of wrapping data ( attributes) and the code ([[method]]s) that operates on the data into a single unit called a [[Class]]. It restricts direct access to some of the [[Object]]'s components and provides controlled access through methods.
- [[private]] members : Data within a [[Class]] that is hidden from outside code and can only be accessed or modified through [[public]] [[method]] (getters/ setters).
- [[public]]  members : Functions that allow controlled interaction with the [[private]] data.
```Csharp
public class BankAccount {
	private double balance;
	// Encapsulated data
public BankAccount(double initialBalance) {
		balance = initialBalance;
	}
public void Depsoite(double amount) {
		balance += amount;
	}
public double GetBalance()  {
	return balance;
	}
}
```
Here, `balance` is [[private]] and can only be modified using `Deposit` and `GetBalance` [[method]]s, ensuring encapsulation.