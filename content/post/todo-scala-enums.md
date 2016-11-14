+++
date = "2016-11-14T19:38:05+02:00"
draft = true
title = "Enums in Scala"
tags = [ "code", "scala", "basics" ]
categories = [ "Scala" ]
+++

TODO...

Alternative with Case Objects
-----------------------------

```scala
object SolarSystemPlanets {

  sealed abstract class Planet(
    val orderFromSun : Int,
    val name         : String,
    val mass         : Kilogram,
    val radius       : Meter) extends Ordered[Planet] {

      def compare(that: Planet) = this.orderFromSun - that.orderFromSun

      lazy val surfaceGravity = G * mass / (radius * radius)

      def surfaceWeight(otherMass: Kilogram) = otherMass * surfaceGravity

      override def toString = name
  }

  case object MERCURY extends Planet(1, "Mercury", 3.303e+23, 2.4397e6)
  case object VENUS   extends Planet(2, "Venus",   4.869e+24, 6.0518e6)
  case object EARTH   extends Planet(3, "Earth",   5.976e+24, 6.3781e6)
  case object MARS    extends Planet(4, "Mars",    6.421e+23, 3.3972e6)
  case object JUPITER extends Planet(5, "Jupiter", 1.9e+27,   7.1492e7)
  case object SATURN  extends Planet(6, "Saturn",  5.688e+26, 6.0268e7)
  case object URANUS  extends Planet(7, "Uranus",  8.686e+25, 2.5559e7)
  case object NEPTUNE extends Planet(8, "Neptune", 1.024e+26, 2.4746e7)

  import EnumerationMacros._
  val planets: Set[Planet] = sealedInstancesOf[Planet]

  type Kilogram = Double
  type Meter   = Double
  private val G = 6.67300E-11 // universal gravitational constant  (m3 kg-1 s-2)
}
```
