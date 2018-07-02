---
title: 設計您的配接器的秘訣 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bb60988-4e48-4654-9cf4-512dd7c97239
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 306cb2ae9aeca57804a57f0dfa8c1de1bfd0025d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982679"
---
# <a name="tips-for-designing-your-adapter"></a>設計配接器的秘訣
本節包含配接器開發人員在設計配接器時所學習到的提示及秘訣。  
  
## <a name="handler-properties-should-be-strings-if-used-as-default-configurations"></a>處理常式屬性在當做預設組態使用時必須是字串  
 似乎能吸引使用 XSD 產生的處理常式屬性工作表上的屬性，預設值為他們**位置**屬性因為如果未設定值**位置**執行階段自動會使用處理常式中設定的值。 但這會產生幾個問題，使得這種做法不是那麼好用。  
  
 問題在於我們不知道是否應該覆寫這個提供給執行階段的值。 這麼做的方法，通常是先瞭解定義這個值的 NULL，然後再對該值執行測試。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中使用 XSD 屬性工作表時，之所以產生問題，是因為只有字串才支援 NULL。 即使您希望透過使用這種 NULL 測試，將配接器設定為預設設定，而且願意將配接器限制為字串類型，這還是會在使用者介面上，讓人有格格不入的感覺。  
  
 XSD 產生的屬性工作表僅支援 NULL 屬性的設定，以滑鼠右鍵按一下  屬性，此時**使合約失效？** 操作功能表隨即出現，並將屬性可以設為 NULL。 至於該屬性是否為 NULL，並沒有視覺回應可供參考。  
  
## <a name="considerations-for-implementing-schema-generation-wizards"></a>實作結構描述產生精靈的考量  
 程式設計人員還是喜歡針對強型別 (Strongly Typed) 物件模型撰寫程式碼。 在程式碼中操作 XML，起初可能很麻煩，而且容易出錯。 但是藉助一些訣竅並巧妙運用 .NET Framework 提供的支援，事情可以在大幅簡化之後迎刃而解。  
  
#### <a name="do-not-create-xml-documents-with-string-concatenation"></a>不要使用字串串連方式建立 XML 文件  
 嘗試透過字串串連及列印陳述式，在記憶體中產生 XML，是在處理 XML 時會犯的其中一個最糟糕的錯誤。 這會消耗大量的 CPU 時間和記憶體。 即使是微不足道的 XML 片段，使用如 XmlWriter 或「文件物件模型」(DOM) 等工具，都會比使用上述方法來得容易。 如果您要使用 XmlWriter，請勿使用原始資料寫入功能，因為這個寫入器會丟失文件的狀態。  
  
 在執行階段中，使用 XmlWriter 勝過使用 XML DOM，因為與 DOM 大量消耗記憶體的問題有關。 然而，這在設定階段或設計階段中，多半不成問題。 使用 DOM 有助於使用 XPATH 查詢，而後者將會是另一項好用的工具。  
  
#### <a name="consider-defining-the-skeleton-of-your-xml-document-as-a-resource"></a>考慮將 XML 文件架構定義為資源  
 如果您要透過設計工具製作大型 XML 文件，而產生的這份文件一律遵循相同的基本結構，請考慮將整個 XML 架構檔案當做資源置於專案中，以便您在需要編輯它時進行變更。  
  
 將程式碼載入 DOM 中，然後使用 XPATH 挑出您要加入的節點，在文件的架構上添增必要的具體內容。 此時，您是在建立 Web 服務描述語言 (WSDL) 檔案。 精靈將 WSDL 架構檔案儲存在資源中，並加入產生的 XML 結構描述定義 (XSD) 子組件。 它會搭配 XPath 使用 selectNode 來尋找正確的父代。 由於這是使用者介面程式碼，所以沒有效能上的問題，而產生的實作非常明瞭、穩固且易於維護。  
  
## <a name="consider-placing-processing-steps-in-the-biztalk-pipeline"></a>考慮將處理步驟置於 BizTalk 管線中  
 一般而言，Microsoft 建立的配接器會將基於訊息格式的處理移出配接器並置入 BizTalk 管線。 結構化的非 XML 資料來源配接器就是最好的範例。  
  
 在這種情況下，配接器只負責取得資料，而 BizTalk 管線則用來剖析資料，並將它轉換成相對的 XML。 這麼做的好處是，管線元件本身會成為架構中可重複使用的項目。  
  
## <a name="make-adapter-behavior-configurable"></a>讓配接器行為變得可設定  
 我們從 MQSeries 配接器 Beta 程式中學到了一個教訓，那就是並非所有的客戶都對相同的行為方式感到滿意。 這在處理錯誤和排序時，更是如此。 藉由讓客戶可以設定配接器的行為模式，我們解決了這個問題。 您可以指定配接器是否要支援排序、要將失敗狀況移至擱置的佇列，或者要讓失敗造成配接器本身停止處理並停用。 當客戶必須為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 撰寫外部的複雜協調流程或指令碼來達到相同效果時，讓這類行為變得可設定，將可以明顯簡化客戶經歷的過程。  
  
## <a name="support-correlation-with-message-queues"></a>支援與訊息佇列的相互關聯  
 許多傳訊平台都支援訊息標頭中的相互關聯識別碼概念，以便支援應用程式層級要求-回應實例。 例如，MQSeries、MSMQ 和 SQL Service Broker。 將外部傳訊系統的要求-回應模式，與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的傳送-回應配接器相提並論，似乎頗具說服力。 但這並不合理，因為沒有考慮到交易所在的位置。 說得明白些，對外部傳訊系統進行的傳送作業必須先完成交易式認可，佇列的另一端才看得到資料。 此外，接收作業也必須是不同的交易。  
  
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，解決的方法如下：  
  
- 使用協調流程中的相互關聯集  
  
- 設定兩個不同的連接埠： 一個用於傳送，一個用於接收  
  
  在簡單的情況下，協調流程會依據配接器指定與訊息有關的相互關聯識別碼。 這個識別碼會傳遞給配接器做為訊息上的內容屬性。 在更複雜的情況下，這個實例會要求外部傳訊系統配置識別碼。 在此情況下將它傳遞回從傳送埠至協調流程的回應訊息。 此回應訊息只是將識別碼傳回，並不是真正的訊息回應。  
  
> [!NOTE]
>  在協調流程引擎中會發生競爭情形，以致真正的訊息回應可能搶先傳送作業中的識別碼回應。 這種競爭情形必須在協調流程內部自行處理。