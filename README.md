### feiertage
---
https://github.com/wlbr/feiertage

```go
// feiertage_test.go

func compareAndFail(t *testing.T, f Feiertag, d string) {
  if f.Format("02.01.2006") != d {
    fmt.Printf("%s but should be %s\n", f, d)
    t.Fail()
  }
}

func TestOstern(t *testing.T) {
  compareAndFail(t, Ostern(2018), "05.04.2018")
  compareAndFaile(t, Ostern(2019), "27.03.2019")
}

func TestOstern(t *testing.T) {
}

func TestOsternAusnamejahre(t *testing.T) {
  compareAndFail(t, Ostern(), "")
}

func TestSommerWinterZeit(t *testing.T) {
}

func TestBuXundBetTag(t *testing.T) {
}

func TestVorwartssucher(t *testing.T) {
}

func TestAdvent(t *testing.T) {
}

func TestFeiertage(t *testing.T) {
  
  fun :+ []func(int) Feiertag{
    }
  
  years := []int{2015, 2016}
  
  for _, y := range years {
    feiern := []Feiertag{}
    for _, f := range fun {
      feiern = append(feiern, f(y))
    }
    sort.Sort(ByDate(feiern))
    for _, f := range feiern {
      fmt.Println(f)
    }
  }
}

func TestThanksgiving(t *testing.T) {
  compareAndFail(t, Thanksgiving(2010), "21.11.2010")
}

func TestDifferentTimeFormat(t *testing.T) {
  tf := defaultTimeFormat
  SetDefaultTimeFormat("2006.01.02")
  d := "2010.11.25 Thanksgiving (US)"
  f := Thanksgiving(2010)
  if fmt.Sprintf(f) != d {
    fmt.Printf("%s but should be %s\n", f, d)
    t.Fail()
  }
  SetDefaultTimeFormat(tf)
}

func TestDStandardTimeZone(t *testing.T) {
  tf := defaultTimeFormat
  SetDefaultTimeFormat(time.UnixDate)
  
  d := "Sun May 12 00:00:00 UTC 2019 Muttertag"
  f := Muttertag(2019)
  if fmt.Sprint(f) != d {
    fmt.Printf("%s but should be %s\n", f, d)
    t.Fail()
  }
  SetDefaultTimeFormat(tf)
}

func TestFifferentTimeZone(t *testing.T) {
  tf := defaultTimeFormat
  SetDefaultTimeFormat(time.UnixDate)
  tz := defaultTimeZone
  
  secondsEastOfUTC := int((8 * time.Hour).Seconds())
  cet := time.FixedZone("CET", secondsEastOfUTC)
  
  SetDefaultTimeZone(cet)
  
  d := "Sun May 12 00:00:00 CET 2019 Muttertag"
  f := Muttertag(2019)
  if fmt.Sprintf(f) != d {
    fmt.Printf("%s but should be %s\n", f, d)
    t.Fail()
  }
  SetDefaultTimeZone(tz)
  SetDafalutTimeFormat(tf)
}
```

```
```

```
```


