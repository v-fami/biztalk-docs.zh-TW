---
title: 迴圈運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19886ccb-4642-48a4-b93e-563640ea828b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ce2b66fd796708a0e8b24ee05e3a0b043af6808
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22262838"
---
# <a name="looping-functoid"></a>迴圈運算質

## <a name="overview--example"></a>概觀 （& s) 範例
**迴圈** 運算質結合多個記錄或欄位在來源結構描述至目的結構描述中的單一記錄。  
  
 下圖顯示 **迴圈**運算質在對應中用來結合位址從兩個不同調查收集到單一主要地址清單。  
  
> [!NOTE]
>  **迴圈** 和 **值對應 （簡維）** 運算質不應在一起。 如果一起使用，就會產生編譯的對應，假設沒有來源迴圈相依性的目標節點下方的 **迴圈** 運算質。  
  
 ![迴圈運算質用法的對應。](../core/media/loopingfunctoid.gif "loopingfunctoid")  
  
 **FoodSurvey** 和 **[flowersurvey]** 將來源結構描述的迴圈記錄對應至迴圈 **位址** 記錄目的結構描述。 如果輸入執行個體訊息有三個 **FoodSurvey** 記錄和兩個 **[flowersurvey]** 記錄 **迴圈**運算質結合這些元件，以建立五個 **位址** 輸出執行個體訊息中的記錄。  
  
 以下程式碼為範例輸入執行個體訊息。  
  
```  
<ns0:Surveys xmlns:ns0="http://LoopingFunctoid.Surveys">  
    <FoodSurvey Name="Karin Zimprich" Address="345 N 63rd St" City="Boston" State="MA" PostalCode="07485" />  
    <FoodSurvey Name="Wendy Wheeler" Address="7890 Broadway" City="Columbus" State="OH" PostalCode="46290" />  
    <FoodSurvey Name="Florian Voss" Address="1234 Main St" City="Denver" State="CO" PostalCode="97402" />  
    <FlowerSurvey Name="Kelly Focht" Address="456 1st Ave" City="Miami" State="FL" PostalCode="81406" />  
    <FlowerSurvey Name="Jim Kim" Address="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103" />  
</ns0:Surveys>  
```  
  
 此輸入執行個體訊息會產生下列輸出執行個體訊息時由前面的圖中的對應。  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Name="Karin Zimprich" Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458"/>  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290"/>  
    <Address Name="Florian Voss" Street="1234 Main St" City="Denver" State="CO" PostalCode="97402"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103"/>  
</ns0:MasterAddresses>  
```  
  
 **FoodSurvey** 和 **[flowersurvey]** 訊息位址已結合。 結合的訊息不會指出每個位址的來源。 如果您想要追蹤來源，加入 **來源** 屬性設定為 **位址** 記錄 **MasterAddress** 結構描述和對應的常數值。 若要設定此值，連線 **FoodSurvey** 欄位至新 **來源** 欄位。 在連接器一行，修改 **連結屬性** &#124; **編譯器** &#124; **來源連結** 「 複製名稱 」 的屬性。 重複此程序 **[flowersurvey]** 欄位。 從上述程序重新處理輸入訊息會產生下列輸出：  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Name="Karin Zimprich" Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458" Source="FoodSurvey"/>  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290" Source="FoodSurvey"/>  
    <Address Name="Florian Voss" Street="1234 Main St" City="Denver" State="CO" PostalCode="97402" Source="FoodSurvey"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406" Source="FlowerSurvey"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103" Source="FlowerSurvey"/>  
</ns0:MasterAddresses>  
```  

## <a name="relationships-with-nodes"></a>與節點關聯性

 在節點之間的關聯性影響行為的 **迴圈** 運算質。 例如，連結的子節點和其來源結構描述中的父系 **迴圈** 運算質可防止在目的節點建立。  
  
 運算質也會受來源節點間的關係影響。 將運算質連接至來源節點的非同層級子欄位 **迴圈** 運算質可能會產生非預期的結果。 比方說，使用 **字串串連** 運算質結合 **FoodSurvey** 名稱 欄位和 **flowersurvey** 的地址名稱欄位中的 位址 欄位 **MasterAddress** 會產生下列輸出執行個體訊息︰  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://LoopingFunctoid.MasterAddresses">  
    <Address Street="345 N 63rd St" City="Boston" State="MA" PostalCode="07458"/>  
    <Address Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290"/>  
    <Address Street="1234 Main St" City="Denver" State="CO" PostalCode="97402"/>  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406"/>  
    <Address Name="Jim Kim" Street="567 2nd Ave" City="Seattle" State="WA" PostalCode="98103"/>  
</ns0:MasterAddresses>  
```  
  
 請注意如何 **名稱** 欄位缺少 **FoodSurvey** 來源訊息卻存在 **[flowersurvey]** 來源訊息。  
  
> [!IMPORTANT]
>  將運算質連接至來源節點的子欄位 **迴圈** 運算質可能會產生非預期的結果，如果來源節點不是同層級。  
  
 **迴圈** 運算質是功能強大的建構，可用來建立條件式迴圈，並將結構描述對應到類別目錄。 也有一些重疊的效果 **迴圈** 運算質路徑，您需要列入考量。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [條件式迴圈](../core/conditional-looping.md)  
  
-   [目錄的一般結構描述](../core/flat-schema-to-catalog.md)  
  
-   [迴圈路徑](../core/loop-paths.md)  
  
## <a name="see-also"></a>另請參閱  
 **表格迴圈運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]