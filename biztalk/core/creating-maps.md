---
title: 建立對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc9f8ad1-4aad-4866-8aa4-4877fdc5e5f9
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e27f4fae142f4c781f95be148ec80e2dff51383
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003095"
---
# <a name="creating-maps"></a>建立對應
BizTalk 對應工具的主要使用者介面會顯示在索引標籤內[!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗。 此顯示分成三個窗格。 左窗格以樹狀結構顯示來源結構描述， 而右窗格會將目的結構描述顯示為樹狀結構。 中間窗格則會將格線顯示為多頁。 若要指出您想要如何將資料從來源結構描述對應至目的結構描述，則您可以在想要對應的記錄與欄位之間繪製線條。 這些線條稱為*連結*，而且是指定之資料的對應最基本的方式。 如需連結記錄和欄位的詳細資訊，請參閱 <<c0> [ 對應中的連結](../core/links-in-maps.md)。  
  
 如果您需要實作更進階的對應方法，可以使用運算質。 運算質是位於 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 工具箱內 BizTalk 對應工具索引標籤上的工具， 可以讓您建立對應來執行較複雜的作業，例如：  
  
- 在來源結構描述的兩個欄位中新增值，然後將結果放置在目的結構描述的一個欄位中。  
  
- 計算迴圈記錄中之一個欄位的平均值，然後將結果放置在目的結構描述的一個欄位中。  
  
- 視您的商務需求，適當地撰寫自訂指令碼來處理執行個體資料。  
  
  如需運算質的詳細資訊，請參閱[運算質在對應中的](../core/functoids-in-maps.md)。  
  
  BizTalk 對應工具可以支援許多不同的對應實例，範圍從簡單的父-子關係到詳細且複雜的記錄迴圈和階層。 建立對應時請考量下列事項：  
  
- BizTalk 對應工具不支援合併與排序。  
  
- 如果來源和目標結構描述結構差異很大，則可能無法在單一對應中執行轉換。 您可能需要採用雙重對應。  
  
- **迴圈**運算質有彈性且功能強大，但您無法中斷反覆運算時偵測到來源結構描述的值變更來啟動目標迴圈的下一個反覆項目。  
  
- 您可以宣告的變數中的方法外**指令碼處理**運算質，會導致變數會出現在對應的存留期內的範圍。 因此，您可以使用**指令碼處理**」 運算質轉換的各個範圍區之間保留值。  
  
  處理的所有資料[!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在執行階段必須是 XML 格式。 所有非 XML 資料都必須轉譯成相等的 XML 格式，才能進行對應。 同樣地，當對應程序完成時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用對應作業的輸出來建立檔案格式，而這是接收資料的交易夥伴或應用程式可辨識的檔案格式。  
  
  BizTalk 對應工具包含一個編譯器。 此工具層次的元件會產生可延伸樣式表語言轉換 (XSLT)，且必須有 XSLT 才能將輸入執行個體訊息轉換或轉譯成輸出執行個體訊息。  
  
  本節提供使用 BizTalk 對應工具在兩個結構描述之間建立對應的工作特定資訊。 假設您已開啟 BizTalk 對應工具，且已選擇您的來源與目的結構描述。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [管理專案中的對應](../core/managing-maps-within-projects.md)  
  
-   [使用連結指定記錄和欄位對應](../core/using-links-to-specify-record-and-field-mappings.md)  
  
-   [使用運算質建立更多複雜對應](../core/using-functoids-to-create-more-complex-mappings.md)  
  
-   [如何建立不含對應](../core/how-to-create-a-map-without-maps.md)  
  
-   [管理預設對應工具的行為使用\<mapsource\>](../core/managing-default-mapper-behavior-using-mapsource.md)