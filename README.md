#include <iostream>
#include <cmath>
#include <complex>

class QuadraticSolver {
private:
    double a, b, c;
    double discriminant;

public:
    QuadraticSolver(double coeffA, double coeffB, double coeffC) : a(coeffA), b(coeffB), c(coeffC) {
        discriminant = b * b - 4 * a * c;
    }
    void solve() {
        if (a == 0) {
            std::cout << "Error: 'a' cannot be zero for a quadratic equation." << std::endl;
            return;
        }

        std::cout << "Discriminant (D) = " << discriminant << std::endl;

        if (discriminant > 0) {
            double root1 = (-b + sqrt(discriminant)) / (2 * a);
            double root2 = (-b - sqrt(discriminant)) / (2 * a);
            std::cout << "D > 0: Two distinct real roots." << std::endl;
            std::cout << "Root 1: " << root1 << std::endl;
            std::cout << "Root 2: " << root2 << std::endl;
        } else if (discriminant == 0) {
           
            double root = -b / (2 * a);
            std::cout << "D = 0: One real root (repeated)." << std::endl;
            std::cout << "Root: " << root << std::endl;
        } else {
            std::complex<double> root1 = (-b + sqrt(std::complex<double>(discriminant))) / (2 * a);
            std::complex<double> root2 = (-b - sqrt(std::complex<double>(discriminant))) / (2 * a);
            std::cout << "D < 0: Two complex roots." << std::endl;
            std::cout << "Root 1: " << root1 << std::endl;
            std::cout << "Root 2: " << root2 << std::endl;
        }
    }
};

int main() {
    double a, b, c;
    std::cout << "Enter coefficient a: ";
    std::cin >> a;
    std::cout << "Enter coefficient b: ";
    std::cin >> b;
    std::cout << "Enter coefficient c: ";
    std::cin >> c;

    QuadraticSolver solver(a, b, c);
    solver.solve();

    return 0;
}
