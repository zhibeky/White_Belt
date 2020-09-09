#include <iostream>
#include <vector>
#include <algorithm>
#include <sstream>
#include <set>
#include <map>
#include <exception>
using namespace std;
class Rational{
public:
  Rational(){
    num = 0;
    den = 1;
  }
  Rational(int numerator, int denominator){
    stringstream s;
    if(denominator == 0) {
      throw invalid_argument("Invalid argument");
    }
    if(denominator < 0){
      if(numerator < 0){
        numerator = abs(numerator);
        denominator = abs(denominator);
      }
      else{
        denominator = abs(denominator);
        numerator = numerator - 2 * numerator;
      }
    }
    if(numerator == 0) denominator = 1;

    int nod = Nod(abs(numerator), abs(denominator));
    num = numerator / nod;
    den = denominator / nod;
  }
  bool operator==(const Rational rat1) const {
    if(rat1.num == num && rat1.den == den)
      return true;
    else return false;
  }
  Rational operator+(const Rational rat1) const {
    int d = rat1.den * den;
    int n = num * rat1.den + rat1.num * den;
    return {n, d};
  }
  Rational operator-(const Rational rat) const {
    int d = rat.den * den;
    int n = num * rat.den - rat.num * den;
    return {n, d};
  }
  Rational operator*(const Rational rational) const {
    int n = num * rational.num;
    int d = den * rational.den;
    return {n, d};
  }
  Rational operator/(const Rational rational) const {
    stringstream s;
    if(rational.num == 0) {
      throw domain_error("Division by zero");
    }
    int n = num * rational.den;
    int d = den * rational.num;
    return {n, d};
  }

  int Numerator() const{
    return num;
  }
  int Denominator() const{
    return den;
  }
private:
  int num;
  int den;
  int Nod(int a, int b){
    while(a > 0 && b > 0){
      if(a > b)
        a %= b;
      else b %= a;
    }
    return a + b;
  }
};
bool operator<( const Rational& r1, const Rational& r2 ){
  return (r1.Numerator() * r2.Denominator() < r1.Denominator() * r2.Numerator());
}
istream& operator>>(istream& in, Rational& rat){
  int p, q;
  if(in >> p && in.ignore(1) && in >> q)
    rat = {p, q};
  return in;
}
ostream& operator<<(ostream& out, const Rational& rat){
  out << rat.Numerator() << "/" << rat.Denominator();
  return out;
}

int main() {

  try {
    Rational r1, r2;
    char ch;
    cin >> r1 >> ch >> r2;
    if(ch == '+') cout << r1 + r2;
    else if(ch == '-') cout << r1 - r2;
    else if(ch == '*') cout << r1*r2;
    else if(ch == '/') cout << r1/r2;
  } catch(invalid_argument& ex) {
    cout << ex.what() << endl;
  }
  catch(domain_error& ex){
    cout << ex.what() << endl;
  }
    return 0;
}
