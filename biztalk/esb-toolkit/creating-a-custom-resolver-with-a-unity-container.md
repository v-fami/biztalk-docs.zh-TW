---
title: "建立自訂解析程式與 Unity 容器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6f95f5e-64dd-4cc6-802f-0c5fd6a01c91
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15952ef3cc8f19eaa5de1a4155d0dc7f6e03c5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-resolver-with-a-unity-container"></a>使用 Unity 容器中建立自訂的解析程式
您可以建立自訂的解析程式使用[Unity 應用程式區塊](http://go.microsoft.com/fwlink/?LinkId=188286)(Unity) ([http://go.microsoft.com/fwlink/?LinkId=188286](http://go.microsoft.com/fwlink/?LinkId=188286)) 執行階段相依性插入的解析邏輯和中繼資料來源。
  
 **事實提供者**  
  
 事實提供者是實作的類別執行個體**IFactProvider**介面。 此介面會公開三個不同的多載方法，名為**RegisterFact**。 這個方法會在訊息中，解析程式組態中，並在某些情況下，為管線的內容，並傳回的物件。 這個物件可能是擷取自以某種方式輸入資訊，它可能是一種計算的某種形式，或它可能查閱來自外部來源。 事實提供者所傳回每個物件可以稱為事實，而且通常會新增至清單解析容器，供稍後使用事實轉譯器。  
  
 Unity 解析程式可能有零個或多個事實提供者，可以加入或移除在任何單一組態變更的時間。  
  
 下列程式碼是範例事實提供者中所包含的邏輯。 此程式碼也可以找到 ESB ItineraryStaticFactProvider.cs 檔案中。Resolver.Itinerary.Facts 專案。 它是從解析程式的連接字串中收集的名稱和版本的行程路線靜態解析程式中的元件。  
  
```csharp  
public object RegisterFact(IBaseMessage message, IPipelineContext pipelineContext, Dictionary\<string, string> resolverContents)  
{  
    return GetItineraryFactFromResolver(resolverContents);  
}  
  
private static object GetItineraryFactFromResolver(Dictionary\<string, string> resolverContents)  
{              
    if (resolverContents == null)  
        throw new ArgumentNullException("resolverContents");  
  
    ItineraryFact itineraryFact = new ItineraryFact();  
    itineraryFact.Name = ResolverMgr.GetConfigValue(resolverContents, true, "name");  
    string version = ResolverMgr.GetConfigValue(resolverContents, false, "version");  
    if (!string.IsNullOrEmpty(version))  
    {  
        EventLogger.Write(string.Format("Version set with value {0}.", version));  
        itineraryFact.SetVersion(version);  
    }  
    return itineraryFact;  
}  
```  
  
 **事實轉譯器**  
  
 事實轉譯器是實作的類別執行個體**IFactTranslator**介面。 此介面會公開單一方法，名為**TranslateFact**。 這個方法會採用包含一份事實並稍後再將解析程式使用事實轉譯器所傳回的解析程式字典的物件陣列中。 事實轉譯器會負責處理事實的事實提供者所提供有意義的方式，然後填入解析程式字典項目。  
  
 Unity 解析程式可能有零個或多個事實轉譯器可以新增或移除在任何單一組態變更的時間。  
  
 下列程式碼是範例事實轉譯器中所包含的邏輯。 此程式碼也可以找到 ESB ItineraryStaticFactTranslator.cs 檔案中。Resolver.Itinerary.Facts 專案。 它是路線靜態解析程式執行資料庫查詢依名稱，並選擇性地版本所收集的行程路線 XML 中的元件。  
  
```csharp  
public void TranslateFact(object[] facts, Dictionary\<string, string> factDictionary)  
{  
    #region Argument Check  
    if (null == facts) throw new ArgumentNullException("fact");  
    if (null == factDictionary) throw new ArgumentNullException("factDictionary");  
    #endregion  
  
    #region Local Variables  
    Version version = new Version(1, 0);                         
    #endregion  
    try  
    {  
        foreach (object fact in facts)  
        {  
            if (fact is ItineraryFact)  
            {  
                ItineraryFact targetFact = (ItineraryFact)fact;  
                factDictionary.Add(_FactKeyItineraryName, targetFact.Name ?? string.Empty);  
                if (null != targetFact.Version)  
                {  
                    factDictionary.Add(_FactKeyItineraryVersion, targetFact.Version.ToString(2) ?? string.Empty);  
                    version = targetFact.Version;  
                }  
  
                string xml = null;  
  
                if (targetFact.Version != null)  
                {  
                    xml = _repositoryProvider.GetItinerary(targetFact.Name, version.Major, version.Minor);  
                }  
                else  
                {  
                    xml = _repositoryProvider.GetItinerary(targetFact.Name);  
                }  
                if (!string.IsNullOrEmpty(xml))  
                {  
                    factDictionary.Add(_FactKeyItinerary, xml);  
                }  
  
                break;  
            }  
        }  
    }  
    #region Exception Handling  
    catch (System.Exception)  
    {  
        throw;  
    }              
    #endregion  
}  
#endregion  
```  
  
 **解決容器**  
  
 解析容器是類別，實作**IResolveContainer**介面。 通常，它也會實作**IResolveProvider**介面。 **IResolveContainer**介面會公開單一方法，名為**初始化**會採用**IUnityContainer**。 容器傳遞至這個方法會包含所有的相依性 (也就是一個類別的執行個體**IFactProvider**和**IFactTranslator**，和任何所需的型別) 所需的若要完成其處理程序解析程式。  
  
 下列程式碼是實作的範例**IResolveContainer**介面。 此程式碼也可以找到 ESB StaticItineraryResolveContainer.cs 檔案中。Resolver.Itinerary 專案。  
  
```csharp  
#region IResolveContainer Members  
  
private static IUnityContainer Container;  
  
// <summary>  
// This is used by the Unity resolver to initialize the current   
// object with the Unity container.  
// </summary>  
// <param name="container">Unity container used for dependency   
// injection.</param>  
// <remarks>  
// The container used is the ITINERARY container, although this is   
// configurable in Esb.config.  
// </remarks>  
  
public void Initialize(IUnityContainer container)  
{  
  if (container == null)  
    throw new ArgumentNullException("container");  
  
  Container = container;  
}  
#endregion  
```  
  
 在解析容器中，實作**解決**方法**IResolveProvider**介面，就必須逐一查看所有的事實提供者和 Unity 中的事實轉譯器若要讓每個工作來執行處理作業的容器。  
  
 下列程式碼是邏輯解決容器中所包含的範例。 此程式碼也可以找到 ESB StaticItineraryResolveContainer.cs 檔案中。Resolver.Itinerary 專案。  
  
```csharp  
public Dictionary\<string, string> Resolve(ResolverInfo resolverInfo,  
    XLANGMessage message)  
{  
    #region Argument Check  
    if (String.IsNullOrEmpty(resolverInfo.Config))  
        throw new ArgumentNullException("resolverInfo.Config");  
    if (String.IsNullOrEmpty(resolverInfo.Resolver))  
        throw new ArgumentNullException("resolverInfo.Resolver");  
    if (null == message)  
        throw new ArgumentNullException("message");  
    #endregion Argument Check  
  
    return ResolveStatic(resolverInfo.Config, resolverInfo.Resolver,  
        (factProvider, resolverContent) =>   
            factProvider.RegisterFact(message, resolverContent)  
     );  
}          
  
private Dictionary\<string, string> ResolveStatic(string config, string resolver,   
    Func<IFactProvider, Dictionary\<string, string>, object> RegisterFact)  
{  
    try  
    {  
        EventLogger.Write(string.Format("Received {0} value in ITINERARY STATIC resolver.", config));  
  
        Dictionary\<string, string> queryParams =  
                ResolverMgr.GetFacts(config, resolver);  
  
        List<object> facts = new List<object>();  
  
        foreach (IFactProvider factProvider in Container.ResolveAll<IFactProvider>())  
        {  
            facts.Add(RegisterFact(factProvider, queryParams));  
        }  
  
        Dictionary\<string, string> resolverDictionary = new Dictionary\<string, string>();  
  
        object[] convertedFacts = facts.ToArray();  
  
        foreach (IFactTranslator translator in Container.ResolveAll<IFactTranslator>())  
        {  
            translator.TranslateFact(convertedFacts, resolverDictionary);  
        }  
  
        return resolverDictionary;  
    }  
    catch (System.Exception ex)  
    {  
        EventLogger.Write(MethodInfo.GetCurrentMethod(), ex);  
        throw;  
    }  
}  
```  
  
 **設定自訂的 Unity 解析程式**  
  
 若要設定自訂的 Unity 解析程式，相同的設定步驟是指套用時建立自訂的解析程式。不過，還有一些額外的設定必須包含正確註冊元件組成的解析程式。  
  
 首先，在底下的解析程式宣告，Esb.config 檔案**resolverConfig**節點必須新增具有下列兩個屬性：  
  
-   **unitySectionName**。 這個屬性包含組態檔，其中包含 Unity 應用程式區塊; 設定中的組態區段的名稱根據預設，此屬性的值是**esb.resolver**。  
  
-   **unityContainerName**。 此屬性會包含您的自訂解決器的特定 Unity 組態中所定義的 Unity 容器的名稱。  
  
 下列 XML 是必要的組態的範例**解析程式**節點。  
  
```xml  
<resolver name="ITINERARY-STATIC" type="Microsoft.Practices.ESB.Resolver.Unity.ResolveProvider, Microsoft.Practices.ESB.Resolver.Unity, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22">  
     <resolverConfig>  
          <add name="unitySectionName" value="esb.resolver" />  
          <add name="unityContainerName" value="ITINERARY" />  
     </resolverConfig>  
</resolver>  
```  
  
 下列 XML 是底下所需之設定的範例**esb.resolver**節點。  
  
```xml  
<typeAliases>  
     \<!-- Lifetime manager types -->  
     <typeAlias alias="singleton" type="Microsoft.Practices.Unity.ContainerControlledLifetimeManager, Microsoft.Practices.Unity, Version=1.2.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
     \<!-- std type providers -->  
     <typeAlias alias="string" type="System.String, mscorlib"/>  
     <typeAlias alias="int" type="System.Int32, mscorlib"/>  
     \<!-- repository providers -->  
     <typeAlias alias="IRepositoryProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.Repository.IRepositoryProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="SqlRepositoryProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.DataAccess.SqlRepositoryProvider, Microsoft.Practices.ESB.Resolver.Itinerary.DataAccess, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     \<!-- fact providers -->  
     <typeAlias alias="IFactProvider" type="Microsoft.Practices.ESB.Resolver.Facts.IFactProvider, Microsoft.Practices.ESB.Resolver.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="IFactTranslator" type="Microsoft.Practices.ESB.Resolver.Facts.IFactTranslator, Microsoft.Practices.ESB.Resolver.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryStaticFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryStaticFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryHeaderFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryHeaderFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ResolutionFactProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ResolutionFactProvider, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="DefaultFactTranslator" type="Microsoft.Practices.ESB.Resolver.Facts.DefaultFactTranslator, Microsoft.Practices.ESB.Resolver.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryFactTranslator" type="Microsoft.Practices.ESB.Resolver.Itinerary.Facts.ItineraryFactTranslator, Microsoft.Practices.ESB.Resolver.Itinerary.Facts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     \<!-- resolve providers -->  
     <typeAlias alias="IResolveProvider" type="Microsoft.Practices.ESB.Resolver.IResolveProvider, Microsoft.Practices.ESB.Resolver, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
     <typeAlias alias="ItineraryResolveProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.BREItineraryResolverContainer,Microsoft.Practices.ESB.Resolver.Itinerary, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22 "/>  
     <typeAlias alias="StaticItineraryResolveProvider" type="Microsoft.Practices.ESB.Resolver.Itinerary.StaticItineraryResolveContainer,Microsoft.Practices.ESB.Resolver.Itinerary, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22 "/>  
</typeAliases>  
<containers>  
     <container name="ITINERARY">  
          <types>  
               <type type="IResolveProvider" mapTo="StaticItineraryResolveProvider" />  
               <type type="IRepositoryProvider" mapTo="SqlRepositoryProvider" name="CurrentRepositoryProvider">  
                    <lifetime type="singleton" />  
                    <typeConfig extensionType="Microsoft.Practices.Unity.Configuration.TypeInjectionElement,Microsoft.Practices.Unity.Configuration, Version=1.2.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35">  
                         <constructor>  
                              <param name="connectionStringName" parameterType="string">  
                                   <value value="ItineraryDb"/>  
                              </param>  
                              <param name="cacheManagerName" parameterType="string">  
                                   <value value="Itinerary Cache Manager"/>  
                              </param>  
                              <param name="cacheTimeout" parameterType="string">  
                                   <value value="120" />  
                              </param>  
                         </constructor>  
                    </typeConfig>  
               </type>  
               <type type="IFactProvider" mapTo="ResolutionFactProvider" name="ResolutionFactProvider"  />  
               <type type="IFactProvider" mapTo="ItineraryHeaderFactProvider" name="HeaderFactProvider"  />  
               <type type="IFactProvider" mapTo="ItineraryStaticFactProvider" name="StaticFactProvider"  />  
               <type type="IFactTranslator" mapTo="DefaultFactTranslator" name="DefaultFactTranslator">  
                    <lifetime type="singleton" />  
               </type>  
               <type type="IFactTranslator" mapTo="ItineraryFactTranslator" name="ItineraryFactTranslator">  
                    <lifetime type="singleton" />  
                    <typeConfig extensionType="Microsoft.Practices.Unity.Configuration.TypeInjectionElement,Microsoft.Practices.Unity.Configuration, Version=1.2.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35">  
                         <constructor>  
                              <param name="repositoryProvider" parameterType="IRepositoryProvider">  
                                   <dependency name="CurrentRepositoryProvider"/>  
                              </param>  
                         </constructor>  
                    </typeConfig>  
               </type>  
          </types>  
     </container>  
</containers>  
```  
  
 如需在中是必要的組態**esb.resolvers**  節點，請參閱[Unity 應用程式區塊的來源結構描述](http://go.microsoft.com/fwlink/?LinkId=188288)([http://go.microsoft.com/fwlink/?LinkId = 188288](http://go.microsoft.com/fwlink/?LinkId=188288)) MSDN 上。  
  
 **建立自訂的 Unity 解析程式**  
  
 **若要建立自訂的 Unity 解析程式**  
  
1.  （選擇性）實作的類別，以建立組件或組件**IFactProvider**介面，並包含**RegisterFact**提供進行解析所需資訊的方法。  
  
2.  （選擇性）實作的類別，以建立組件或組件**IFactTranslator**介面，並包含**TranslateFact**會轉譯到索引鍵/值組內提供的事實的方法解析程式的字典。  
  
3.  建立組件實作的類別與**IResolveContainer**和**IResolveProvider**介面，且包含**解決**驗證的方法解析程式組態收集事實提供者的所有事實、 執行任何特殊的處理，並使用事實轉譯器轉譯和傳回翻譯的事實執行個體**字典**類別。  
  
4.  註冊解決器將它加入 Esb.config 組態檔使用**\<解析程式 >**元素包含做為根 moniker**名稱**屬性和完整格式組件名稱為**類型**屬性。  
  
5.  這個解析程式加入 Esb.config 檔案 Unity 特有的組態。  
  
6.  （選擇性）建立結構描述定義的根 moniker 和查詢參數，並再將它儲存在 ESB。Schemas.Resolvers 資料夾。 名稱應該遵循現有的 ESB 命名慣例。這表示它應使用的名稱加上"_Resolution.xsd"的根 moniker。  
  
7.  （選擇性）從新的結構描述產生類別，並將它儲存在自訂解決器組件中。 這將會公開自訂解析程式中的型別的參數。  
  
8.  在全域組件快取中註冊的所有組件。