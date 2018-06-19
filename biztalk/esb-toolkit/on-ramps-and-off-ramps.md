---
title: 在坡道提升和關閉坡道提升 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0cce5d2-f16f-4bda-94ac-20c4f457cfc7
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0aafa69315dba07219ad8510c77cdc9de2d4bce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294558"
---
# <a name="on-ramps-and-off-ramps"></a>在坡道提升和關閉坡道提升
在環境中其中[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]是部署，BizTalk 接收位置負責接收 ESB 目的地的訊息指 「 上手。 」 若要設定 ESB 上手的標準 BizTalk 接收位置，接收位置關聯其中一個管線工具組的一部分，並正確設定來決定，或讀取的行程該管線元件輸入的訊息，根據您的案例。  
  
 ESB"匝道 」 對應到 BizTalk 動態傳送埠。 處理行程時，值會升級為使用系統 Properties.xsd 結構描述的相關訊息內容屬性。 BizTalk 發行-訂閱機制會使用這些升級屬性來路由訊息，以透過動態傳送埠 （匝道） 以完成訊息傳遞。  
  
 下表列出在-坡道提升所提供的[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。  
  
|名稱|訊息交換模式|**說明**|  
|----------|------------------------------|---------------------|  
|ESB。ItineraryServices|單向|ASMX 上手。SOAP 標頭中預期 ESB 路線內容。|  
|ESB。ItineraryServices.Response|要求-回應|ASMX 上手。SOAP 標頭中預期 ESB 路線內容。|  
|ESB。ItineraryServices.WCF|單向|Windows Communication Foundation (WCF) 上手。需要 ESB 路線參考 SOAP 標頭中。|  
|ESB。ItineraryServices.Response.WCF|要求-回應|WCF 上手。需要 ESB 路線參考 SOAP 標頭中。|  
|ESB。ItineraryServices.Generic.WCF|單向|WCF 上手。預期只要求訊息。|  
|ESB。ItineraryServices.Generic.Response.WCF|要求-回應|WCF 上手。預期只要求訊息。|  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]在-坡道提升不 ASMX 應該設定為選取 ESB 行程。 如需如何選取 ESB 行程的詳細資訊，請參閱[使用管線元件，選取現有的行程](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md)。