---
title: 發現無法辨識的訊息類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad4094bf-af00-4d5c-9661-7c8abcb1b722
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14a76219470f971d2c83e11dabfec7fa912dcb5f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992863"
---
# <a name="unrecognised-message-type"></a>無法辨識的訊息類型
## <a name="details"></a>詳細資料  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                UnRecognizedMessageType                                 |
|  訊息文字   |                   無法辨識的訊息類型。 無法進一步處理。                   |

## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為沒有文件結構描述文件類型的交易集在該交換中，已部署或 BizTalk Server 無法判斷文件類型從交易集識別項代碼、 版本和命名空間。  

## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  

- 部署文件類型的結構描述文件的交換中交易集，然後再重新傳送交換。  

- 請確認下列值，定義有效的結構描述： 對於 X12，目標命名空間、 版本/版次和文件類型;對於 EDIFACT，目標命名空間、 訊息版本號碼、 訊息版次號碼和訊息類型。 如需詳細資訊，請參閱的 < 結構描述探索 > 一節中的 「 合作對象解析、 結構描述探索和已接收 EDI 訊息的授權 」 主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。
