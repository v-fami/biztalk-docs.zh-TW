---
title: "值對應運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Value Mapping functoids
- functoids, empty tags
- Concatenate functoids
ms.assetid: 3dd626fb-3bf6-4ede-9fd2-ddae5a54d178
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 038d59827a62c9f4e83879ec7cf2e0b47fd738f4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="value-mapping-functoid"></a>值對應運算質
**值對應**運算質會傳回其第二個參數的值，如果第一個參數為 true。 運算質的一般用途是將欄位的屬性變更為記錄的屬性。 若要藉由將多個記錄轉換成單一記錄扁平化的輸入訊息的一部分，請使用[值對應 （簡維） 運算質](../core/value-mapping-flattening-functoid.md)。  
  
 下圖顯示具有對應**值對應**運算質用於記錄屬性變更欄位的屬性。  
  
 ![](../core/media/valuemappingfunctoid.gif "valuemappingfunctoid")  
值對應運算質對應  
  
 下列程式碼會顯示輸入執行個體訊息中其中成對的名稱和值會指派給**名稱**和**值**屬性。  
  
```  
<ns0:Root xmlns:ns0="http://ValueMapping.WeatherIn">  
    <Record>  
        <Field Name="WindSpeed" Value="5"/>   
        <Field Name="Temperature" Value="20" />  
    </Record>  
    <Record>  
        <Field Name="WindSpeed" Value="15" />  
        <Field Name="Temperature" Value="18" />  
    </Record>  
</ns0:Root>  
```  
  
 上述對應可將此訊息轉換成一組，其中值會指派給不同記錄中具有對應名稱的屬性。  
  
```  
<ns0:Root xmlns:ns0="http://ValueMapping.WeatherOut">  
    <Record WindSpeed="5"/>  
    <Record Temperature="20"/>  
    <Record WindSpeed="15"/>  
    <Record Temperature="18"/>  
</ns0:Root>  
```  
  
 **等於**運算質會測試的值**名稱**屬性。 第一個**等於**值的運算質會測試**名稱**為"WindSpeed"。 當**名稱**為"WindSpeed，"第一個**等於**運算質會傳回**True**。 這項目，接著，可讓**值對應**設定的值的運算質**WindSpeed**輸出執行個體訊息中的屬性。  
  
## <a name="suppressing-the-creation-of-empty-tags"></a>抑制空白標記的建立  
 若要抑制空白標記，請使用值對應運算質來控制是否要建立標記。 如果該值評估為 True，就會建立目的地欄位；否則，就不會建立目的地欄位。 在迴圈案例中，請使用邏輯運算質，並將它連接到目的地記錄或欄位。 如果情況評估為 False，就不會建立標記。 如需範例，請參閱[條件式迴圈](../core/conditional-looping.md)。  
  
## <a name="forcing-the-creation-of-empty-tags"></a>強制空白標記的建立  
 若要強制建立空白標記，您可以將值連結的目的地欄位的值屬性中**Concatenate**運算質到目的地欄位。  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，便可選取來強制產生空白標記"\<空\>"在目的地欄位的 Value 屬性的值。 在此情況下，該欄位會以空值建立。  
  
## <a name="see-also"></a>請參閱  
 [值對應 （簡維） 運算質](../core/value-mapping-flattening-functoid.md)   
 [如何新增值對應運算質至對應](../core/how-to-add-value-mapping-functoids-to-a-map.md)   
 [進階運算質](../core/advanced-functoids.md)