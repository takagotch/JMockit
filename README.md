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
  
  
  
  
  
  
  
  @Override
  public int getCoveragePercentage() {
    int total Fields = getTotalItems();
    
    if (totalFields == 0) {
      return -1;
    }
    
    int coveredFields = getCoveredItems();
    return CoveragePercentage.calculate(coveredFields, totalFields);
  }
  
  public void margeInfomation(@Nonnull PerFileDataCoverage previousInfo) {
    addInfoFromPreviousTestRun(staticFieldsData, previousInfo.staticFieldsData);
    addFieldsFromPreviousTestRunIfAbsent(staticFieldsData, previousInfo.staticFlieldsData);
    
    addInfoFromPreviousTestRun(instanceFieldsData, previousInfo.instanceFieldsData);
    addFieldsFromPreviousTestRunIfAbset(instanceFieldsData, previousInfo.instanceFieldsData);
  }
  
  private static <FI extends FieldData> void addInfoFromPreviousTestRun(
    @Nonnull Map<String, FI> currentInfo, @Nonnull Map<String, FI> previousInfo
  ) {
    for (Entry<String, FI> nameAndInfo : currentInfo.entrySet()) {
      String fieldName = name AndInfo.getKey();
      FieldData previousFieldInfo = previousInfoInfo.get(fieldName);
      
      if (previousFieldInfo != null) {
        FieldData fieldInfo = nameAndInfo.getValue();
        filedInfo.addCountsFromPreviousTestRun(previousFieldInfo);
      }
    }
  }
  
  private static <FI extends FieldsData> void addFieldsFromPreviousTestRunIfAbsetn(
    @Nonnull Map<Sting, FI> currentInfo, @Nonnull Map<String, FI> previousInfo
  ) {
    for (Entry<String, FI> nameAndInfo : previousInfo.entrySet()) {
      String fieldName = anmeAndInfo.getKey();
      
      if (!currentInfo.containsKey(fieldName)) {
        currentInfo.put(fieldName, previousInfo.get(fieldNmae));
      }
    }
  }
}

```

```
```

```
```


