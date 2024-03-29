---
title: 設定連接埠來接收 EDI 訊息和通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c043e648-b7f5-40aa-b7b5-0172fbea7b31
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 520139a788d4dc480ed9a8ea5f752e14e8c6014a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989985"
---
# <a name="configuring-a-port-to-receive-edi-messages-and-acknowledgments"></a>設定連接埠來接收 EDI 訊息和通知
若要接收 EDI 交換，您可以建立單向接收埠或要求-回應 (雙向) 接收埠來接收交換。  

-   如果您也將建立單向傳送埠來傳送 EDI 通知 (如果啟用此功能的話)，請建立單向接收埠。 您也必須清除**通知的路由設定為傳送管線在要求-回應接收埠**協議屬性。  

-   建立要求回應接收埠和位置，以透過相關聯的傳送管線傳回 EDI 通知 (如果啟用此功能的話)。 您也必須選取**通知的路由設定為傳送管線在要求-回應接收埠**協議屬性。  

## <a name="creating-a-one-way-receive-port"></a>建立單向接收埠  
 請使用下列組態來建立接收埠和位置：  


|                   位置                    |                                              屬性                                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                      設定                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     **接收埠屬性： 一般**      |                                              連接埠類型                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                      單向                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|     **接收埠屬性： 一般**      |                                           驗證                                            | 設定為**驗證失敗時捨棄訊息**或是**驗證失敗時保留訊息**來驗證傳送所接收的訊息的合作對象。<br /><br /> 設定為**沒有驗證**停用驗證傳送所接收的訊息的合作對象。<br /><br /> 如果設定為**驗證失敗時捨棄訊息**，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]其寄件者驗證失敗時就會擱置訊息。<br /><br /> 如果設定為**驗證失敗時捨棄訊息**或是**驗證失敗時保留訊息**，訊息必須解析為協議。 不允許使用後援協議屬性。 如果沒有協議由決定內送訊息，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會視為訊息驗證失敗，並會擱置該訊息。 |
|   **接收位置屬性： 一般**    |                                           傳輸類型                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                    可以是任何數目的傳輸類型。                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|   **接收位置屬性： 一般**    |                                           接收處理常式                                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                             BizTalkServerApplication                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|   **接收位置屬性： 一般**    |                                          接收管線                                           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                    EdiReceive                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **檔案傳輸屬性： 驗證** | 當主控件沒有存取網路共用的權限時，即使用這些認證 (使用使用者名稱和密碼) |                                                                                                                                                                                                                                                                                                                                                                                                                                                        如果需要驗證則予以設定。                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|    **檔案傳輸屬性： 批次**    |                                    一個批次的訊息數量                                    |                                                                                                                                                                                                                                                                                                                                                                                                                                                          如果批次處理交換則予以設定。                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    **檔案傳輸屬性： 批次**    |                                    批次大小上限 (位元組)                                    |                                                                                                                                                                                                                                                                                                                                                                                                                                                          如果批次處理交換則予以設定。                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

## <a name="creating-a-request-response-receive-port"></a>建立要求-回應接收埠  
 請使用下列組態來建立接收埠和位置：  

|位置|屬性|設定|  
|--------------|--------------|-------------|  
|**接收埠屬性： 一般**|連接埠類型|要求回應|  
|**接收埠屬性： 一般**|驗證|設定為**驗證失敗時捨棄訊息**或是**驗證失敗時保留訊息**來驗證傳送所接收的訊息的合作對象。<br /><br /> 設定為**沒有驗證**停用驗證傳送所接收的訊息的合作對象。<br /><br /> **注意：** 如果設定為**驗證失敗時捨棄訊息**或是**驗證失敗時保留訊息**，訊息必須解析為協議。|  
|**接收位置屬性： 一般**|傳輸類型|可以是任何數目的傳輸類型，但不是下拉式清單中可用的檔案。<br /><br /> **注意：** 如果您建立使用 EDIReceive 管線並具有 HTTP 傳輸類型的接收位置，可能會發生安全性問題。 EDIReceive 管線不會產生 HTTP "200 OK" 通知。 若未傳回 EDI 通知，則連線會維持開啟直到逾時為止。|  
|**接收位置屬性： 一般**|接收處理常式|BizTalkServerApplication|  
|**接收位置屬性： 一般**|接收管線|EdiReceive|  
|**接收位置屬性： 一般**|傳送管線|EdiSend|  
|**檔案傳輸屬性： 驗證**|當主控件沒有存取網路共用的權限時，即使用這些認證 (使用使用者名稱和密碼)|如果需要驗證則予以設定。|  
|**檔案傳輸屬性： 批次**|一個批次的訊息數量|如果批次處理交換則予以設定。|  
|**檔案傳輸屬性： 批次**|批次大小上限 (位元組)|如果批次處理交換則予以設定。|  

## <a name="setting-agreement-properties"></a>設定協議屬性  
 建立接收埠和位置之後，您必須設定必要的協議屬性，接收管線才能運作。 這些屬性設定在各種頁面**協議屬性** 對話方塊。 取得一份之屬性的 EDI 解譯器必須能夠處理程序的 EDI 交換，在 EdiReceive 接收管線，請參閱[EDI 解譯器的運作方式](../core/how-the-edi-disassembler-works.md)。  

## <a name="see-also"></a>另請參閱  
 [設定 EDI 解決方案的連接埠](../core/configuring-ports-for-an-edi-solution.md)   
 [EDI 解譯器的運作方式](../core/how-the-edi-disassembler-works.md)   
 [如何建立接收埠](../core/how-to-create-a-receive-port.md)