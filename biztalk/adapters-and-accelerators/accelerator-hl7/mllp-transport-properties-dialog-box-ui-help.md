---
title: MLLP 傳輸屬性對話方塊 UI 說明 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.mllp.transportproperties
ms.assetid: 2a41aaeb-a91d-4d89-ac8a-1cfe48ab4cd4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b9856b7fbbac5dd9d6a4f809e369e586d95a31b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962092"
---
# <a name="mllp-transport-properties-dialog-box-ui-help"></a>MLLP 傳輸屬性對話方塊 UI 說明
您使用**MLLP 傳輸屬性**對話方塊來設定參數傳送和接收最少的較低層通訊協定 (MLLP) 配接器。 您可以設定網路連線參數 MLLP 傳輸屬性中的 傳送埠或接收位置使用 MLLP 傳輸類型。  
  
 如需 MLLP 屬性的詳細資訊，請參閱[傳送和接收配接器的組態參數](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)。  
  
## <a name="uielement-list"></a>UIElement 清單  
 在**MLLP 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
#### <a name="block-characters"></a>區塊字元  
 區塊字元參數都必須括住 HL7 訊息接收或傳送到 MLLP 配接器的特殊字元。 這些字元會形成區塊以下列格式： \<SB\>*DDD*\<EB\>\<CR\>，其中*DDD*代表訊息資料， \<SB\>是開始區塊的字元， \<EB\>是 end 區塊的字元，並\<CR\>歸位字元，會傳回。  
  
|使用|動作|  
|--------------|----------------|  
|**\<CR\>歸位字元**|位元組值 （以十六進位格式），您用於歸位字元 （第二個位元組包裝函式之後結束位元組）。 選擇性。|  
|**\<EB\> End 區塊的字元**|您用於結束位元組 （訊息結尾包裝函式） 的位元組值。 ASCII \<FS\>，例如\<1c\>。|  
|**\<SB\>開始區塊字元**|您用於啟動位元組 （訊息標頭包裝函式） 的位元組值。 ASCII \<VT\>，例如\<0b\>。|  
  
#### <a name="deliverymode"></a>DeliveryMode  
 您可以使用傳遞模式參數，控制是否執行個體的檔案傳遞的順序，或超出序列 （依順序，順序）。 每個接收位置有它自己傳遞順序的執行個體的檔案。  
  
|使用|動作|  
|--------------|----------------|  
|排序的傳遞|**MLLP 接收**:<br /><br /> 如果您設定**排序的傳遞**屬性**FALSE** （預設值） 的執行個體檔案將不會傳遞順序。 將第一次傳遞推入佇列之後更大的執行個體檔案較小的執行個體檔案。 設定**排序的傳遞**屬性**TRUE**、 依序傳遞執行個體的檔案。|  
  
#### <a name="network-connection-parameters"></a>網路連線參數  
 您可以使用網路連線參數來建立連接，透過網路包括註解、 連線名稱、 主機名稱、 連接埠識別碼、 接收逾時，和傳送逾時。  
  
|使用|動作|  
|--------------|----------------|  
|**註解**|連接描述。 選擇性。|  
|**連接名稱**|受監視連接的名稱。 建議的名稱是唯一。 名稱會包含此連線的效能計數器執行個體的名稱。|  
|**主控件**|**MLLP 接收**:<br /><br /> 選擇性。 指定要接聽連入連線的本機介面。 依預設會接聽，所有的本機介面上。<br /><br /> **MLLP 傳送**:<br /><br /> 指定您要連接的特定業務 (LOB) 電腦的 IP 位址或 NetBIOS 名稱。|  
|**持續連線**|**MLLP 接收**:<br /><br /> 設定**持續連線**屬性**FALSE** （預設值），以關閉的連接，連接之後閒置逾時期限。 設定**持續連線**屬性**True**，若要讓連線保持開啟。<br /><br /> **MLLP 傳送**:<br /><br /> 設定**持續連線**屬性**FALSE**以關閉連接，如果逾時期限內收到回應，或已超過逾時期限。 設定**持續連線**屬性**True** （預設值），若要讓連線保持開啟。<br /><br /> 請參閱[持續連線和接收的逾時值](../../adapters-and-accelerators/accelerator-hl7/mllp-transport-properties-dialog-box-ui-help.md#persistentConnectionAndReceiveTimeout)，和[連接埠類型和連接狀態](../../adapters-and-accelerators/accelerator-hl7/mllp-transport-properties-dialog-box-ui-help.md#portTypeConnectionStatus)如需詳細資訊。|  
|**[通訊埠]**|**MLLP 接收**:<br /><br /> 本機連接埠上接聽的識別碼。<br /><br /> **MLLP 傳送**:<br /><br /> 您要連線的遠端連接埠識別碼。|  
|**傳送逾時**|**MLLP 傳送**:<br /><br /> 傳送配接器時傳送訊息時，所等待的時間上限之後傳送的通訊端將會逾時。在到期時，BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會重試訊息。<br /><br /> 此外，發生同步作業的傳送埠，接收來自 LOB 的通知 (ACK) 的最長時間。|  
|**接收逾時**|**MLLP 接收**:<br /><br /> 接收配接器接收的訊息時，在其後的接收通訊端會逾時等待的時間上限。在到期時，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會關閉連線。<br /><br /> 此外，發生同步作業的接收位置，以便將通知傳送到 LOB 的最大時間。|  
|**請求回應已啟用**|**MLLP 傳送**:<br /><br /> Yes/no。 啟用接收相同的 TCP 連接上認可。|  
|**送出接收位置的 URI 來通知**|**MLLP 傳送**:<br /><br /> 認可收到相同的 TCP 連線所在的接收位置的 URI 會傳遞至 MessageBox 資料庫。|  
  
#####  <a name="persistentConnectionAndReceiveTimeout"></a>持續連線和接收的逾時值  
 如**MLLP 接收**下, 表顯示可能的值的結果**持續連線**和**接收逾時**值。  
  
|**持續連線**|**接收逾時**|結果|  
|-------------------------------|-------------------------|------------|  
|**FALSE**|>0|收到的訊息或逾時期間經過之後，就會關閉連線。|  
|**FALSE**|0|造成錯誤狀況:"接收逾時值不應該發生持續連線 FALSE 的零。"|  
|**為 TRUE**|0|連接不會中斷。|  
|**為 TRUE**|<>0|造成錯誤狀況: 「 接收逾時值應該是零，如果持續性連線 TRUE 」。|  
  
 如**MLLP 傳送**下, 表顯示可能的值的結果**持續連線**和**接收逾時**值。  
  
|**持續連線**|**傳送逾時**|結果|  
|-------------------------------|----------------------|------------|  
|**FALSE**|0 或 > 0|收到的回應或逾時期間經過之後，就會關閉連線。|  
|**為 TRUE**|0 或 <> 0|連接不會中斷。 **傳送逾時**值不會影響連線的狀態。|  
  
#####  <a name="portTypeConnectionStatus"></a>連接埠類型和連接狀態  
 下表顯示不同的傳送埠的連線狀態時類型持續連線的設定和請求回應變更。  
  
|傳送連接埠類型|持續連線|請求回應|連線狀態|  
|--------------------|---------------------------|----------------------|-----------------------|  
|靜態單向|TRUE|否|會保持開啟狀態|  
|靜態單向|TRUE|是|會保持開啟狀態|  
|靜態單向|FALSE|否|Closed|  
|靜態單向|FALSE|是|Closed|  
|靜態請求回應|FALSE|是|會保持開啟狀態|  
|靜態請求回應|TRUE|是|會保持開啟狀態|  
|靜態請求回應|FALSE|否|Closed|  
|靜態請求回應|FALSE|是|Closed|  
  
## <a name="see-also"></a>請參閱  
 [處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [MLLP 的接收配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [MLLP 傳送配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [設定傳送埠來接收 ACK](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)