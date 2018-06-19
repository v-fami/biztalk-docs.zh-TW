---
title: 設定 XML 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52851901-8374-412f-9c29-83845d8d4861
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d791de9b6fe90ebb850874026e8d52e49732f32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233822"
---
# <a name="configuring-the-xml-file"></a>設定 XML 檔案
當您安裝「企業單一登入」(SSO) 時，名為 ENTSSO.xml 的 XML 檔案會安裝在 Extensions 目錄中。 您可以編輯這個檔案，定義 ENTSSO「管理代理程式」(MA) 所有執行個體的組態。  
  
 這個檔案看起來類似如下：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<sso>  
  
  <SourceMA name="RACFMA1" objectType="person" attribute="uid"/>  
  <SourceMA name="ACF2" objectType="person" attribute="uid"/>  
  
  <ENTSSOMA name ="ENTSSOMA1" adma="ADMA1" deleteAll="true">  
    <Application name="AppForRACF1A" sourceMA="RACFMA1" create="true" delete="true"/>  
    <Application name="AppForRACF1B" sourceMA="RACFMA1" create="true" delete="false"/>  
  </ENTSSOMA>  
  
  <ENTSSOMA name ="ENTSSOMA2" adma="ADMA1" deleteAll="true">  
    <Application name="AppForACF2" sourceMA="ACF2"/>  
  </ENTSSOMA>  
  
</sso>  
```  
  
## <a name="xml-elements-and-attributes"></a>XML 項目和屬性  
 下列清單說明 XML 檔案中定義的項目和屬性。 請注意，這個檔案中的所有項目和屬性都區分大小寫。  
  
 **項目： ENTSSO** -定義單一 ENTSSO MA 執行個體的組態。 允許有多個 ENTSSO 項目。  
  
 **屬性： 名稱**-定義 ENTSSO 管理代理程式的執行個體名稱，而且必須符合 ENTSSO 管理代理程式執行個體中 Microsoft Identity Integration Server (MIIS) 的名稱。  
  
 **屬性： adma** -定義 ENTSSO 管理代理程式執行個體將會使用 Active Directory 管理代理程式的執行個體名稱。 Active Directory「管理代理程式」可提供 Windows 網域名稱和 Windows 使用者名稱以供對應。 這個 Active Directory「管理代理程式」執行個體名稱必須與 MIIS 中的 Active Directory「管理代理程式」執行個體名稱相符。  
  
 **屬性： deleteAll** -選擇項，預設值是`true`。 若此屬性設定為 `true`，則刪除某個 Windows 識別時，該 Windows 識別的所有對應都將會從所有 ENTSSO 應用程式中刪除。  
  
 **項目： 應用程式**-定義 SSO 分支機構應用程式和外部的管理代理程式之間的關聯性。 允許有多個 `Application` 項目。  
  
 **屬性： 名稱**-定義 SSO 分支機構應用程式的名稱。 這個應用程式必須已經存在於 ENTSSO 系統內。  
  
 **屬性： sourceMA** -定義來源 （外部） 的執行個體名稱將用來提供此應用程式的對應中的外部 UserId 的管理代理程式。 這個外部「管理代理程式」執行個體名稱必須與 MIIS 中的外部 MA 執行個體名稱相符。  
  
 **屬性： 建立**-選擇項，預設值是`true`。 此屬性會定義是否應該為這個應用程式建立對應。  
  
 **屬性： 刪除**-選擇項，預設值是`true`。 此屬性會定義是否應該為這個應用程式刪除對應。  
  
 **項目： SourceMA** -選擇性。 此項目會識別特定來源 (外部)「管理代理程式」執行個體的物件類型和屬性名稱。 如果特定「管理代理程式」沒有這個項目，則會假設為預設物件類型 (“person”) 和屬性名稱 (“uid”)。 允許有多個 `SourceMA` 項目。  
  
 **屬性： 名稱**-來源 （外部） 的名稱管理代理程式。 這個名稱必須至少符合 `sourceMA` 項目的其中一個 `Application` 屬性名稱。  
  
 **屬性： objectType** -選擇項，預設值是`person`。 如果提供外部 UserId 的物件類型名稱不是 `person`，則應在此指定。  
  
 **屬性： 屬性**-選擇項，預設值是`uid`。 如果提供外部 UserId 的屬性名稱不是 `uid`，則可以在此指定。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 ENTSSO 管理代理程式](../core/how-to-use-the-entsso-management-agent.md)