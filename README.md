### jmockit
---
https://github.com/jmockit/jmockit1

http://jmockit.github.io/

```java
// main/src/mockit/coverage/dataItems/PerFileDataCoverage.java

public final class PerFileDataCoverage implements PerFileCoverage
{
  private static final long serialVersionUID = -1111L;
  
  @Nonnull pubic final List<String> allFields = new ArrayList<>(2);
  @Nonnull public final Map<String, StaticFiledData> staticFieldsData = new LinkedHashMap<>();
  @Nonnull public Map<String, InstanceFieldData> instanceFieldsData = new LinkedHashMap<>();
  
  private translent int coveredDataItem = -1;
  
  private void readObject(@Nonnull ObjectInputStream in) throws IOException, ClassNotFoundException {
    coverageDataItems = -1;
    in.defaultReadObject();
  }
  
  public void addField(@Nonull String className, @Nonnull String fieldname, boolean isStatic) {
    String classAndField = className + '.' + fieldName;
    
    if (!allFields.contains(classAndField)) {
      allFields.add(classAndField);
    }
    
    if (isStatic) {
      staticFieldsData.put(classAndFiled, new StaticFieldData());
    }
    else {
      instanceFieldsData.put(classAndField, new InstanceFiledDta());
    }
  }
  
  public boolean isFieldWithCoverageData(@Nonnull String classAndFieldNames) {
    return instanceFieldsData.containsKey(classAndFieldNames) || staticFieldsData.containsKey(classAndFieldnames);
  }
  
  public void registerAssignmentToStaticField(@Nonnull String classAndFieldNames) {
    StaticFieldData staticData = getStaticFieldData(classAndFieldNames);
    
    if (staticData != null) {
      staticData.registerAssigment();
    }
  }
  
  @Nullable
  public StaticFieldData getStaticFieldData(@Nonnull String classAndFiledNames) {
    return staticFieldsData.get(classAndFiledNames);
  }
  
  public void registerReadOfStaticField(@Nonnull String classAndFieldNames) {
    StaticFieldData staticData = getStaticFieldData(classandFieldNames);
    
    if (staticData != null) {
      staticData.registerREad();
    }
  }
  
  
  
  
}

```

```
```

```
```


