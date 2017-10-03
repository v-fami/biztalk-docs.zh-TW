---
title: "擲回 SOAP 例外狀況，從協調流程發佈為 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, SOAP exceptions
- orchestrations, SOAP errors
- Web services, orchestrations
ms.assetid: e1c7cd74-d1c8-4b9d-a418-4601b1f040d7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4ef3d975632b6230cf1e3df299d0d9455f39da0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-throw-soap-exceptions-from-orchestrations-published-as-a-web-service"></a>如何從協調流程發佈為 Web 服務擲回 SOAP 例外狀況
您可以從已發佈為 Web 服務的協調流程擲回 SOAP 例外狀況。 您會將錯誤訊息加入到 SOAP 連接埠中，並傳回該錯誤訊息不是傳回回應。  
  
### <a name="to-throw-a-soap-exception-from-an-orchestration-published-as-a-web-service"></a>若要從發佈為 Web 服務的協調流程擲回 SOAP 例外狀況  
  
1.  將錯誤訊息加入到 SOAP 連接埠類型。 錯誤訊息的訊息類型可以是符合 XML 結構描述 (XSD) 標準的任何結構描述或簡單類型。  
  
    > [!NOTE]
    >  若要傳回字串做為**SoapException**資訊時發生錯誤，您可以使用簡單類型字串做為錯誤訊息類型。  
  
2.  在協調流程中建立錯誤訊息。  
  
3.  使用**傳送**圖形，連結到 SOAP 連接埠對應至錯誤訊息中的錯誤作業。 SOAP 例外狀況會包裝傳回的訊息錯誤。  
  
 如果您的協調流程不會傳回錯誤，使用不同**傳送**傳送標準 SOAP 回應訊息使用一般回應作業的圖形。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤訊息](../core/fault-messages.md)   
 [協調流程發佈為 Web 服務](../core/publishing-an-orchestration-as-a-web-service.md)