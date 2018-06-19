---
title: 訊息修復和新送出服務處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- repairing messages, MrsrRepair orchestration
- orchestrations, MrsrRepair orchestration
- InfoPath forms, valid forms
- messages, BAS
- unparsed messages
- repairing messages, unparsed messages
- messages, unparsed messages
- messages, InfoPath forms
- Business Rule Engine
- MrsrRepair orchestration
- InfoPath forms, messages
- BAS, messages
ms.assetid: fe2ee009-bf63-4bc0-b231-ad8a2633719f
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: add084f335f2ca3bd816af7a743327e77cbecca1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22211198"
---
# <a name="message-repair-and-new-submission-service-processing"></a>訊息修復和新送出服務處理
MrsrRepair 協調流程會處理所有訊息修復和新送出作業，包括下列處理：  
  
-   需要修復的訊息  
  
-   未剖析的訊息  
  
-   MRSR 網站上建立新的訊息  
  
## <a name="processing-messages-requiring-repair"></a>處理要求修復的訊息  
 如果訊息必須進行修復，協調流程，會收到警示傳入訊息來自反組譯工具。 它只處理來自解譯器的訊息，如果建立或修復設定角色功能。 MrsrRepair 協調流程會訂閱訊息從 MessageBox 具有下列屬性：  
  
```  
A4SWIFT_Failed==true AND  
BTS_Operation=="A4SWIFT_DasmMarkedAsFailed" AND  
A4SWIFT_SwiftBound==true  
```  
  
 輸入連接埠 MrsrRepair 用於 Message Repair 和 New Submission 的協調流程繫結至為 Sts.Outbox.Location 的接收位置。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]安裝程式會安裝此接收位置的預設值。 當使用者提交訊息至 MRSR 站台，此接收位置拾取訊息，並將其傳送至 MrsrRepair 協調流程。  
  
 下表列出有效[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單：  
  
|[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單||||||  
|------------------------------------------------------------------------------|------|------|------|------|------|  
|MT010|MT011|MT012|MT015|MT019|MT020|  
|MT021|MT022|MT023|MT028|MT029|MT030|  
|MT031|MT032|MT035|MT036|MT037|MT039|  
|MT041|MT042|MT043|MT044|MT045|MT046|  
|MT047|MT048|MT049|MT050|MT051|MT052|  
|MT055|MT056|MT057|MT059|MT061|MT062|  
|MT063|MT064|MT065|MT066|MT067|MT068|  
|MT069|MT072|MT073|MT074|MT075|MT076|  
|MT077|MT081|MT082|MT083|MT085|MT087|  
|MT090|MT092|MT094|MT102|MT102PLUS|MT103|  
|MT103Plus|MT104|MT105|MT106|MT107|MT110|  
|MT111|MT112|MT121|MT190|MT191|MT192|  
|MT195|MT196|MT198|MT199|MT200|MT201|  
|MT202|MT203|MT204|MT205|MT206|MT207|  
|MT210|MT256|MT290|MT291|MT292|MT295|  
|MT296|MT298|MT299|MT300|MT303|MT304|  
|MT305|MT306|MT307|MT308|MT320|MT321|  
|MT330|MT340|MT341|MT350|MT360|MT361|  
|MT362|MT364|MT365|MT380|MT381|MT390|  
|MT391|MT392|MT395|MT396|MT398|MT399|  
|MT400|MT405|MT410|MT412|MT416|MT420|  
|MT422|MT430|MT450|MT4555|MT456|MT490|  
|MT491|MT492|MT495|MT496|MT498|MT499|  
|MT500|MT501|MT502|MT503|MT504|MT505|  
|MT506|MT507|MT508|MT509|MT510|MT513|  
|MT514|MT515|MT516|MT517|MT518|MT519|  
|MT524|MT526|MT527|MT528|MT529|MT535|  
|MT536|MT537|MT538|MT540|MT541|MT542|  
|MT543|MT544|MT545|MT546|MT547|MT548|  
|MT549|MT558|MT559|MT564|MT565|MT566|  
|MT567|MT568|MT569|MT574_IRSLST|MT574_W8BENO|MT575|  
|MT576|MT577|MT578|MT579|MT581|MT582|  
|MT584|MT586|MT587|MT588|MT589|MT590|  
|MT591|MT592|MT595|MT596|MT598|MT599|  
|MT600|MT601|MT604|MT605|MT606|MT607|  
|MT643|MT644|MT645|MT646|MT649|MT690|  
|MT691|MT692|MT695|MT696|MT698|MT699|  
|MT700|MT701|MT705|MT707|MT710|MT711|  
|MT720|MT721|MT730|MT732|MT734|MT740|  
|MT742|MT747|MT750|MT752|MT754|MT756|  
|MT760|MT767|MT768|MT769|MT790|MT791|  
|MT792|MT795|MT796|MT798|MT799||  
|MT800|MT801|MT802|MT810|MT812|MT813|  
|MT820|MT821|MT822|MT823|MT824|MT890|  
|MT891|MT892|MT895|MT896|MT898|MT899|  
|MT900|MT910|MT920|MT935|MT940|MT941|  
|MT942|MT950|MT960|MT961|MT962|MT963|  
|MT964|MT965|MT966|MT967|MT970|MT971|  
|MT972|MT973|MT985|Mt986|MT990|MT991|  
|MT992|MT995|MT996|MT998|MT999||  
  
## <a name="processing-unparsed-messages"></a>處理未剖析的訊息  
 如果無法剖析訊息，它會設定適當的旗標，並再將訊息傳送至 MRSR MrsrRepair 協調流程會決定網站收件匣中的修復[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單未剖析的訊息。 當協調流程收到訊息時修復完成後時，它會設定 BTS。作業屬性 」[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_MRSRCompleted"和[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed 屬性設定為 False，然後將訊息路由傳送至 MessageBox。 這些屬性確定，修復未剖析的訊息不會輸入訊息修復程序一次。  
  
 未剖析的修復，稱為**未剖析訊息**。  
  
## <a name="processing-new-messages-created-in-mrsr"></a>處理 MRSR 中建立的新訊息  
 如果 MRSR 站台中建立 MrsrRepair 協調流程所收到的訊息，協調流程會收到警示來自內送訊息[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]（不解譯器），並簽署訊息。  
  
## <a name="common-operations"></a>一般作業  
 不論它們需要修復，無法剖析或新的訊息，MrsrRepair 協調流程會執行一系列的所有訊息上的一般作業。 協調流程執行迴圈，以便執行工作流程，包括重設金鑰驗證每個步驟的一般作業、 建立、 修復及核准。 此協調流程會使用無論部門和角色。  
  
 下列一般步驟如下：  
  
1.  將訊息放置在信封表單中。  
  
2.  傳送訊息至 MRSR 站台。  
  
3.  （使用者動作之後） 接收 MRSR 透過為 Sts.Outbox.Location 的站台的訊息接收位置。 如果發生逾時，協調流程會處理逾時。如果發生逾時或使用者的修復、 驗證、 核准訊息時，雖然[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]修復收件匣，重設為修復階段的工作流程會傳回訊息。  
  
    > [!NOTE]
    >  輸入連接埠 MrsrRepair 用於 Message Repair 和 New Submission 的協調流程繫結至為 Sts.Outbox.Location 的接收位置。 此接收位置必須在 BizTalk 主控件繫結至具有 MRSR 站台安裝的伺服器執行。 主機通常會是 [biztalkserverapplication]，但它可以是不同的主機。 如果是不同的主機，您必須先確認主應用程式繫結至的伺服器擁有 MRSR 站台安裝。  
  
4.  驗證使用者輸入的簽章適當的角色，並儲存該簽章，以確認角色限制。  
  
5.  如果上一個步驟所儲存訊息的內容，比較 MRSR 網站與儲存的訊息從接收的內容。 如果不符合，協調流程就會失敗的訊息。  
  
6.  如果使用者已拒絕所做的變更，請失敗訊息。  
  
7.  如果使用者接受變更，請在訊息上執行 XSD 和 BRE 驗證。  
  
8.  如果適用的話，將移至下一個步驟。  
  
## <a name="customizing-the-repair-orchestration"></a>自訂修復協調流程  
 您可以透過將前置處理或後置處理功能加入自訂 MrsrRepair 協調流程。 例如，您可以新增協調流程的前置處理步驟，或新增協調流程圖形之前現有的傳送 」 圖形，以升級屬性。 不過，您無法建立或變更合約或與 Message Repair 和 New Submission，相關聯的設定檔，因為 MrsrRepair 協調流程不會知道它們的存在。 您無法加入新的角色定義，超過 repairer、 建立者、 驗證器或核准者。 您也無法變更此結構，或將功能加入至協調流程的核心。  
  
## <a name="business-rules-policies"></a>商務規則原則  
 修復程序中，修復協調流程呼叫 BizTalk 商務規則引擎 (BRE) 載入訊息類型，例如 MT103_Master_Policy.xml 主要的原則。 協調流程會將 BRE 傳遞的訊息類型和本文。 訊息的主要原則包含一份訊息類型專屬的其他所有原則。 BRE 會載入所有的訊息類型的原則。 這些原則包含 SWIFT_Reference_Policy、 SWIFT_PartyIdentifier_Policy、 網路規則原則，以及特定訊息類型的驗證原則。 BRE 會執行所有主要的原則，無論錯誤，在所列的原則，並傳回所有的錯誤。