---
title: Loopback |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- agreements, 0A1 agreements
- loopbacks, running
- loopbacks, 0A1 agreements
- loopbacks, about loopbacks
- loopbacks, 0A1 messages
- agreements, loopback agreements
- messages, 0A1 messages
- loopbacks
- Loopback utility
- loopbacks, syntax
- 0A1 messages
- loopbacks, Loopback utility
- syntax [loopbacks]
- agreements, Loopback utility
ms.assetid: b4ebbdac-05be-4dfc-a133-6b752994e85a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 656441fe65e840302928e90ea22e21327fee33cd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978047"
---
# <a name="loopback"></a>回送
您可使用回送公用程式自動產生回送協議，該協議是組織到夥伴協議的鏡像複本。 這讓您可以在單一電腦上，執行組織對夥伴以及夥伴對組織的訊息交換。 您可在具有 0A1 訊息或不具有 0A1 訊息的實例中使用此公用程式。 您可為動作訊息 (非 0A1) 協議或 0A1 協議建立回送協議。  

 您也可以使用此公用程式登錄或取消登錄傳送者角色的主要組織。 當您使用此公用程式來啟用主要組織時，它會建立兩個傳送埠，請\<家用\>。Async 和\<首頁\>。同步處理，組織會使用與合作夥伴進行通訊。  

## <a name="location-in-sdk"></a>SDK 中的位置  
 \<*磁碟機*\>\ Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\  

## <a name="running-loopback"></a>執行回送  

#### <a name="to-run-loopback"></a>若要執行回送  

1.  開啟命令提示字元。  

2.  移至\<*磁碟機*\>\ Program Files (x86) \Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\\。  

3.  在命令提示字元中，輸入**Loopback**，輸入必要和適當的參數，然後按 ENTER 鍵。  

## <a name="syntax-for-loopback"></a>Loopback 的語法  
 以下顯示您可用來啟動此命令列公用程式的語法：  

```  
Loopback [/enable|/disable <home_organization>] [/mirror|/unmirror <agreement_name>] [/NoF <0A1_agreement>]  
```  

## <a name="syntax-description"></a>語法描述  
 下表描述回送公用程式使用之語法的各個部分。  

|**語法**|**說明**|  
|----------------|---------------------|  
|**enable**|為傳送者角色登錄在 <home_organization> 中指定的組織。 它會建立兩個傳送埠，請\<首頁\>。Async 和\<首頁\>。同步協力電腦用來回到主要組織通訊。|  
|**disable**|為傳送者角色取消登錄主要組織。|  
|**home_organization**|要為傳送者角色登錄或取消登錄的夥伴。|  
|**mirror**|建立根據協議中指定的回送協議\< **agreement_name**\>。|  
|**實例**|刪除根據協議中指定的回送協議\< **agreement_name\>**。|  
|**agreement_name**|在回送實例中要建立鏡像或取消鏡像的協議。|  
|**收到的 NoF**|設定組**0A1 協議**屬性的動作訊息協議的 Loopback 公用程式來鏡像\<0A1_agreement\>。 A **/NoF**交換器只能加入至也包含的 Loopback 命令 **/鏡像**切換。|  
|**0A1_agreement**|agreement_name 的鏡像協議要使用的 0A1 協議。 此協議是藉由建立回應者 0A1 協議的鏡像來產生。|  

## <a name="remarks"></a>備註  
 Loopback 公用程式會切換建立回送協議的角色。 如果某個組織在原始協議中是主要組織，則此公用程式會讓它在回送協議中成為夥伴組織。 同樣的，如果組織在原始協議中是夥伴組織，此公用程式就會讓它在回送協議中成為主要組織。 此公用程式也會切換 Home 角色屬性的設定。 如果 Home 角色屬性在原始協議中是啟動者，此公用程式就會讓它成為回應者，反之亦然。 所有其他屬性仍然保持不變。  

 Loopback 公用程式使用與原始協議相同的名稱來命名回送協議，但在前面加上 "loopback:"。 為了避免混淆，命名協議時請勿以 "loopback" 開頭。  

 如果您在已產生回送協議的協議上執行此公用程式，此公用程式就會取消現有的回送協議鏡像，並建立新的回送協議。  

 您需要使用回送公用程式，因為您無法在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中建立鏡像的協議。 您無法在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中建立主要組織、夥伴組織和主要角色屬性都和現有協議的欄位相反，但所有其他欄位卻完全相同的協議。 同樣地，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 也不支援在主控台中直接變更回送協議。 如果您嘗試在主控台中開啟回送協議，將會收到錯誤。 如果您必須對回送協議進行任何變更，請變更原始的協議，然後在該協議上再執行一次回送公用程式，重新產生回送協議。  

> [!IMPORTANT]
>  這個回送實例不支援已簽署的協議。 在此實例中，已簽署的訊息將驗證失敗，因為 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 讓您只能為單一簽章憑證設定一位合作對象。 主要組織和夥伴組織無法使用相同的簽章憑證。 這是 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 中關於使用簽章憑證以唯一識別某個合作對象的限制。 因此，BizTalk 的合作對象無法使用相同的憑證。  

 如需有關回送實作的詳細資訊，請參閱[Loopback 教學課程](../../adapters-and-accelerators/accelerator-rosettanet/loopback-tutorial.md)。  

## <a name="using-loopback-with-0a1-agreements"></a>使用具有 0A1 協議的 Loopback  
 您可以設定回送實例來產生 0A1 (失敗通知) 訊息。 若要這樣做，您必須針對主要組織建立下列協議：要求動作訊息協議、啟動者 0A1 協議，以及回應者 0A1 協議。 接著，您必須在以上每個協議上執行回送公用程式，以便針對夥伴組織建立下列協議：回應動作訊息協議、啟動者 0A1 協議，以及回應者 0A1 協議。 這是必要的，因為您無法使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台建立這些協議。  

 協議的完整集合必須包括下列訊息的協議。 為了示範，動作訊息為 3A4：  

-   Home_to_Partner_3A4 (動作訊息) 協議。 初始化從 HOME 組織到 PARTNER 組織之動作訊息 PIP 的協議。  

-   Home_to_Partner_Initiator_0A1 協議。 初始化從 HOME 組織到 PARTNER 組織之 PIP 0A1 的協議。  

-   Home_to_Partner_Responder_0A1 協議。 接收從 PARTNER 組織到 HOME 組織之 PIP 0A1 的協議。  

-   Loopback:Home_to_Partner_3A4 (回應訊息) 協議。 接收從 HOME 組織到 PARTNER 組織之 PIP 3A4 的協議。  

-   Loopback:Home_to_Partner_Responder_0A1 協議。 初始化從 PARTNER 組織到 HOME 組織之 PIP 0A1 的協議。  

-   Loopback:Home_to_Partner_Initiator_0A1。 接收從 HOME 組織到 PARTNER 組織之 PIP 0A1 的協議。  

## <a name="creating-the-loopback-agreements-for-0a1-messages"></a>建立 0A1 訊息的回送協議  
 如果要建立協議的完整集合，您必須使用回送公用程式在夥伴上建立動作訊息和 0A1 協議。 下表顯示要產生夥伴回送協議所需的 Loopback 作業。 為了示範，本主題在表格中使用 3A4 訊息。  

|步驟|HOME 協議|  
|----------|---------------------|  
|1, 4|Home_to_Partner_3A4<br /><br /> 主要組織：HOME<br /><br /> 夥伴組織：PARTNER<br /><br /> 主要組織角色：啟動者<br /><br /> 0A1 協議：Home_to_Partner_Initiator_0A1<br /><br /> 描述：起始從 HOME 到 PARTNER 之 PIP 3A4 的協議|  
|2|Home_to_Partner_Initiator_0A1<br /><br /> 主要組織：Home<br /><br /> 夥伴組織：Partner<br /><br /> 角色：啟動者<br /><br /> 描述：起始從 HOME 到 PARTNER 之 PIP 0A1 的協議|  
|3|Home_to_Partner_Responder_0A1<br /><br /> 主要組織：Home<br /><br /> 夥伴組織：Partner<br /><br /> 角色：回應者<br /><br /> 描述：接收從 PARTNER 到 HOME 之 PIP 0A1 的協議|  

|步驟|PARTNER 協議 (使用 Loopback.exe 建立鏡像)|  
|----------|--------------------------------------------------------|  
|7|Loopback:Home_to_Partner_3A4<br /><br /> 主要組織：Partner<br /><br /> 合作夥伴： 首頁<br /><br /> 角色：回應者<br /><br /> 0A1 協議： Loopback:Home_to_Partner_Responder_0A1<br /><br /> 描述：接收從 HOME 到 PARTNER 之 PIP 3A4 的協議<br /><br /> 建立回送的回送命令：Loopback /mirror Home_to_Partner_3A4 /NoF Loopback:Home_to_Partner_Responder_0A1|  
|5|Loopback:Home_to_Partner_Responder_0A1<br /><br /> 主要組織：Partner<br /><br /> 合作夥伴： 首頁<br /><br /> 角色：啟動者<br /><br /> 描述：起始從 PARTNER 到 HOME 之 PIP 0A1 的協議<br /><br /> 建立回送的回送命令：Loopback /mirror Home_to_Partner_Responder_0A1|  
|6|Loopback:Home_to_Partner_Initiator_0A1<br /><br /> 主要組織：Partner<br /><br /> 合作夥伴： 首頁<br /><br /> 角色：回應者<br /><br /> 描述：接收從 HOME 到 PARTNER 之 PIP 0A1 的協議<br /><br /> 建立回送的回送命令：Loopback /mirror Home_to_Partner_Initiator_0A1|  

 請執行這些表格中的 Loopback 命令，做為下列程序的一部分。  

#### <a name="to-create-the-agreements-for-a-loopback-scenario-using-0a1-messages"></a>使用 0A1 訊息建立回送實例的協議  

1. 在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台中，建立主要組織將傳送之要求動作訊息的協議。  

2. 建立主要組織將傳送之啟動者 0A1 訊息的協議，並執行下列動作：  


   |         使用         |                  以進行此動作                  |
   |--------------------------|----------------------------------------------|
   |   **我的組織**    |        設為主要組織。         |
   | **夥伴組織** |             設為夥伴。              |
   |      **主要角色**       | 設定為**PIP Failure Notifier (Initiator)**。 |


3. 使用 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台，針對要傳送到主要組織的回應者 0A1 訊息建立協議，並執行下列動作：  


   |         使用         |                      以進行此動作                      |
   |--------------------------|------------------------------------------------------|
   |   **我的組織**    |            設為主要組織。             |
   | **夥伴組織** |                 設為夥伴。                  |
   |      **主要角色**       | 設定為**Failure Report Administrator (Responder)**。 |


4. 使用[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管理主控台中，設定**0A1 協議**主要組織之要求動作訊息協議名稱的啟動者 0A1 協議，主要組織屬性。  

5. 使用回送公用程式，建立夥伴組織將傳送之啟動者 0A1 訊息的協議。 您可以建立主要組織之回應者 0A1 協議的鏡像來完成這個動作。 這會建立新的 「 0A1 」 協議同名**回送：\<0A1 協議名稱\>**。 `My organization`屬性設為夥伴`Partner organization`屬性設為主要組織，而`Home role`屬性是**PIP Failure Notifier (Initiator)**。  

6. 使用回送公用程式，建立夥伴組織將傳送之回應者 0A1 訊息的協議。 您可以建立主要組織之 0A1 啟動者協議的鏡像來完成這個動作。 這會建立新的 「 0A1 」 協議同名**回送：\<0A1 協議名稱\>**。 `My organization`屬性設為夥伴`Partner organization`屬性設為主要組織，而`Home role`屬性是**Failure Report Administrator (Responder)**。  

7. 使用回送公用程式，建立夥伴組織將傳送之回應動作訊息的協議。 在同一個命令中，您必須將 0A1 agreement 屬性設為夥伴的回應者 0A1 協議。 您執行這項操作鏡像要求動作訊息協議，為主要組織，並使用 **/NoF**切換夥伴的回應者 0A1 協議的名稱。 此名稱建立新的回應動作訊息協議**Loopback:\<協議名稱\>**。 `My organization` 屬性會設為夥伴，而 0A1 agreement 屬性則設為夥伴的回應者 0A1 協議。  

## <a name="see-also"></a>另請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [回送教學課程](../../adapters-and-accelerators/accelerator-rosettanet/loopback-tutorial.md)
