---
title: MLLP 傳輸屬性對話方塊 UI 說明 |Microsoft Docs
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
ms.openlocfilehash: c8740ebb1533881e484ab13cdfcce3fc0afb4fbd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971743"
---
# <a name="mllp-transport-properties-dialog-box-ui-help"></a>MLLP 傳輸屬性對話方塊 UI 說明
您使用**MLLP 傳輸屬性**對話方塊來設定參數，請傳送和接收最少的較低層通訊協定 (MLLP) 配接器。 您可以設定網路連線參數 MLLP 傳輸屬性中的其中一個傳送埠或接收位置使用 MLLP 傳輸類型。  

 如需 MLLP 屬性的詳細資訊，請參閱 <<c0> [ 傳送和接收配接器的組態參數](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md)。  

## <a name="uielement-list"></a>UIElement 清單  
 在  **MLLP 傳輸屬性**對話方塊方塊中，執行下列動作：  

#### <a name="block-characters"></a>區塊字元  
 區塊字元參數都必須括住 HL7 訊息已接收或已透過 MLLP 配接器傳送的特殊字元。 這些字元會形成一個區塊以下列格式： \<SB\>*DDD*\<EB\>\<CR\>，其中*DDD*代表訊息資料， \<SB\>是開始區塊的字元， \<EB\>是 end 區塊的字元，並\<CR\>會傳回為換行字元。  

|使用|以進行此動作|  
|--------------|----------------|  
|**\<CR\>歸位字元**|位元組值 （以十六進位格式），您使用的換行字元 （第二個位元組的包裝函式之後結束位元組）。 選擇性。|  
|**\<EB\> End 區塊的字元**|您用於結束位元組 （訊息結尾包裝函式） 的位元組值。 ASCII \<FS\>，例如\<1c\>。|  
|**\<SB\>開始區塊的字元**|您用於起始位元組 （訊息標頭包裝函式） 的位元組值。 ASCII \<VT\>，例如\<0b\>。|  

#### <a name="deliverymode"></a>DeliveryMode  
 您可以使用傳遞模式參數，來控制是否在順序中，或 （依順序，順序） 的順序傳遞執行個體檔案。 每個接收位置有其自己排序執行個體檔案的傳遞。  

|使用|以進行此動作|  
|--------------|----------------|  
|排序的傳遞|**MLLP 接收**:<br /><br /> 如果您設定**排序的傳遞**屬性設**FALSE** （預設值） 的執行個體檔案將不會傳遞順序。 會先傳遞較小的執行個體檔案較大的執行個體檔案之後, 推入佇列。 設定**排序的傳遞**屬性設 **，則為 TRUE**，依序傳遞執行個體的檔案。|  

#### <a name="network-connection-parameters"></a>網路連線參數  
 您可以使用網路連接參數來建立連線，透過網路，包括註解、 連線名稱、 主機名稱、 連接埠識別碼、 接收逾時，和傳送等候逾時。  


|                使用                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          以進行此動作                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              **註解**               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             連接的描述。 選擇性。                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|           **連接名稱**           |                                                                                                                                                                                                                                                                                                                                                                                                                受監視連接的名稱。 建議是唯一的名稱。 包含名稱為此連線的效能計數器執行個體名稱。                                                                                                                                                                                                                                                                                                                                                                                                                |
|                **主控件**                 |                                                                                                                                                                                                                                                                                                                                         **MLLP 接收**:<br /><br /> 選擇性。 指定要接聽連入連線的本機介面。 依預設會接聽本機的所有介面。<br /><br /> **MLLP 傳送**:<br /><br /> 請指定 NetBIOS 名稱或您要連接的營運 (LOB) 電腦的 IP 位址。                                                                                                                                                                                                                                                                                                                                         |
|        **持續連線**        | **MLLP 接收**:<br /><br /> 設定**持續連線**屬性設**FALSE** （預設值），若要連線的閒置逾時期限之後關閉連接。 設定**持續連線**屬性設 **，則為 True**，以保持開啟的連接。<br /><br /> **MLLP 傳送**:<br /><br /> 設定**持續連線**屬性設**FALSE**、 逾時期限內收到回應，或逾時已到時關閉連線。 設定**持續連線**屬性設 **，則為 True** （預設值），以保持開啟的連接。<br /><br /> 請參閱[持續連線和接收的逾時值](../../adapters-and-accelerators/accelerator-hl7/mllp-transport-properties-dialog-box-ui-help.md#persistentConnectionAndReceiveTimeout)，並[連接埠類型和連線狀態](../../adapters-and-accelerators/accelerator-hl7/mllp-transport-properties-dialog-box-ui-help.md#portTypeConnectionStatus)如需詳細資訊。 |
|                **通訊埠**                 |                                                                                                                                                                                                                                                                                                                                                                                                                         **MLLP 接收**:<br /><br /> 本機連接埠上接聽的識別碼。<br /><br /> **MLLP 傳送**:<br /><br /> 您要連線的遠端連接埠識別碼。                                                                                                                                                                                                                                                                                                                                                                                                                         |
|            **傳送等候逾時**             |                                                                                                                                                                                                                                                                    **MLLP 傳送**:<br /><br /> 傳送配接器會在傳送訊息時，等候的時間上限之後傳送的通訊端，將逾時。在到期時，BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 將會重試訊息。<br /><br /> 此外，如果同步作業的傳送埠，接收來自 LOB 的通知 (ACK) 的最長時間。                                                                                                                                                                                                                                                                    |
|           **接收逾時**           |                                                                                                                                                                                                                                                                                 **MLLP 接收**:<br /><br /> 接收配接器接收的訊息，其後的接收通訊端會逾時的等候時間上限。到期後，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]會關閉連線。<br /><br /> 此外，如果同步作業的接收位置，將通知傳送至 LOB 的最長時間。                                                                                                                                                                                                                                                                                 |
|      **請求回應已啟用**       |                                                                                                                                                                                                                                                                                                                                                                                                                                                     **MLLP 傳送**:<br /><br /> 是/否。 能夠在相同的 TCP 連接上接收通知。                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **提交的接收位置 URI 通知** |                                                                                                                                                                                                                                                                                                                                                                                                                 **MLLP 傳送**:<br /><br /> 用以通知接收到相同的 TCP 連線的接收位置的 URI 會傳遞到 MessageBox 資料庫。                                                                                                                                                                                                                                                                                                                                                                                                                 |

#####  <a name="persistentConnectionAndReceiveTimeout"></a> 持續連線和接收逾時值  
 針對**MLLP 接收**下, 表顯示可能的值的結果**持續連線**並**接收逾時**值。  

|**持續連線**|**接收逾時**|結果|  
|-------------------------------|-------------------------|------------|  
|**FALSE**|>0|收到訊息，或逾時期間經過之後，就會關閉連線。|  
|**FALSE**|0|造成錯誤狀況: 「 接收逾時值不應為零，如果持續性連線 FALSE 」。|  
|**TRUE**|0|連線永遠不會中斷。|  
|**TRUE**|<>0|造成錯誤狀況: 「 接收逾時值應為零，如果持續性連線 TRUE 」。|  

 針對**MLLP 傳送**下, 表顯示可能的值的結果**持續連線**並**接收逾時**值。  

|**持續連線**|**傳送等候逾時**|結果|  
|-------------------------------|----------------------|------------|  
|**FALSE**|0 或 > 0|收到的回應或逾時期間經過之後，就會關閉連線。|  
|**TRUE**|0 或 & lt;>0|連線永遠不會中斷。 **傳送等候逾時**值不會影響連線的狀態。|  

#####  <a name="portTypeConnectionStatus"></a> 連接埠類型和連線狀態  
 下表顯示不同的傳送埠的連線狀態時類型持續連線的設定和請求回應變更。  

|傳送連接埠類型|持續連線|請求回應|連線狀態|  
|--------------------|---------------------------|----------------------|-----------------------|  
|靜態單向|TRUE|否|仍保持開啟狀態|  
|靜態單向|TRUE|是|仍保持開啟狀態|  
|靜態單向|FALSE|否|Closed|  
|靜態單向|FALSE|是|Closed|  
|靜態請求回應|FALSE|是|仍保持開啟狀態|  
|靜態請求回應|TRUE|是|仍保持開啟狀態|  
|靜態請求回應|FALSE|否|Closed|  
|靜態請求回應|FALSE|是|Closed|  

## <a name="see-also"></a>另請參閱  
 [處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [MLLP 接收配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md)   
 [MLLP 傳送配接器處理](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md)   
 [設定傳送埠來接收 ACK](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)