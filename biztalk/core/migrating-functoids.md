---
title: 移轉運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- functoids, migrating
- migrating, maps
- Migrating functoids, about Migrating functoids
- Migrating functoids
- Scripting functoids
- migrating, functoids
- migrating, Scripting functoids
ms.assetid: fc5b3ac9-28c6-41df-b779-15a8c3188528
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b01f37551b9d4c1aef13786be7094504f8cee08
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020500"
---
# <a name="migrating-functoids"></a>移轉運算質
當您從舊版的 BizTalk Server 移轉對應至 BizTalk Server 時，對應中包含的任何運算質也會移轉。 如果未包含您所移轉的運算質**指令碼處理**運算質，沒有其他移轉工作所需。 不過如果您的對應包含**指令碼處理**運算質或自訂運算質，您可能必須執行其他步驟。  
  
 在舊版的 BizTalk Server 中，所有的自訂指令碼隨附**指令碼處理**運算質以內嵌方式撰寫。 也就是說，當您建立運算質時，運算質在執行階段呼叫的所有指令碼都與運算質一起儲存。 如果您想要使用不同的運算質使用相同的指令碼，您可以複製並貼上它從某個**指令碼處理**到另一個，或者您的運算質重寫指令碼從零開始。  
  
 在移轉對應時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用運算質複製現有的內嵌指令碼。 不過，並非所有的指令碼可能會正常運作。 BizTalk Server 會使用 Visual Basic.NET 和 JScript.NET，而不是 VBScript 和 JScript 先前版本中使用。 語言的 .NET 版本包含部分語法變更。  
  
> [!NOTE]
>  請務必測試您**指令碼處理**移轉後的運算質。  
  
 您必須重新撰寫自訂運算質。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要使用.NET framework 的自訂運算質。 它不能使用舊版以 COM 為基礎的自訂運算質。 您可以重新撰寫自訂運算質以使用 .NET Framework。 自訂運算質的範例程式碼，請參閱[自訂運算質 （BizTalk Server 範例）](../core/custom-functoid-biztalk-server-sample.md)。  
  
 替代方式是在外部組件中包裝自訂運算質的功能，並呼叫透過這個組件**指令碼處理**運算質。 下節敘述此程序。  
  
### <a name="to-migrate-your-custom-functoids"></a>移轉自訂運算質  
  
1. 使用 .NET 語言 (例如，Microsoft Visual Basic .NET、JScript .NET 或 Microsoft Visual C# .NET) 重新建立運算質的功能。  
  
2. 建立組件以包含新功能。  
  
3. 在全域組件快取 (GAC) 中註冊組件。  
  
   > [!NOTE]
   >  若要在全域組件快取中註冊組件，則組件必須以強式名稱命名並簽章。 如需註冊組件的詳細資訊，請參閱《[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 組合集合》中的＜全域組件快取＞。  
  
4. 之間的對應，包含建立參考**指令碼處理**運算質和組件，其中包含重寫的功能。  
  
5. 設定**指令碼**屬性**指令碼處理**運算質。 此屬性會決定哪些指令碼**指令碼處理**運算質在執行階段期間的呼叫。 您必須將此屬性的值與自訂指令碼已轉換成的語言比對。 如需如何設定 Script 屬性的詳細資訊，請參閱[編輯運算質屬性和輸入參數](../core/editing-functoid-properties-and-input-parameters.md)。 另請參閱[指令碼處理運算質](../core/scripting-functoid.md)。  
  
6. 建置 BizTalk 專案，其中包含地圖**指令碼處理**運算質。  
  
7. 驗證並測試對應。  
  
## <a name="see-also"></a>另請參閱  
 [編輯運算質屬性和輸入的參數](../core/editing-functoid-properties-and-input-parameters.md)   
 [指令碼處理運算質](../core/scripting-functoid.md)