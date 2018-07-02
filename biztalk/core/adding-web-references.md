---
title: 加入 Web 參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BPEL, orchestrations
- orchestrations, BPEL
- Web services, ports
- orchestrations, exporting
- Web services, projects
- Web services, references
- projects, Web services
ms.assetid: 7e40f215-f11a-4151-bcc6-e107bf36b6f6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61923d2cc169184c969ca6e7439b1ee88e9726fb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983735"
---
# <a name="adding-web-references"></a>加入 Web 參考
在您加入 Web 連接埠之前，必須先將 Web 參考加入至 BizTalk 專案。 Web 參考是可供專案使用的 Web 服務描述。 當您新增 Web 參考加入您的專案時，BizTalk 專案會建立協調流程 Web 連接埠類型、 Web 訊息類型、 Reference.map （對應檔案）、 Reference.odx （協調流程檔案）， \< *WebService*\>。disco （探索檔案），並\< *WebService*\>.wsdl （Web 服務描述語言檔） 至您的專案。 如果您的「Web 服務描述語言」(WSDL) 檔案包含結構描述 Web 訊息類型，BizTalk 專案還會將 Reference.xsd 加入至您的專案。  
  
 Web 參考包括：  
  
- Web 服務的「統一資源定位器」(URL)。  
  
- WSDL 檔案，它可提供關於服務的資訊，例如可用的方法、連接埠以及訊息類型。  
  
- 參考對應 (Reference.map)。  
  
  加入 Web 參考時，該 Web 服務的所有 Web 方法都必須與 BizTalk Server 相容。 您不能指定 Web 服務中特定 Web 方法的條件式屬性。  
  
  您使用新增 Web 參考加入您的專案**加入 Web 參考** 對話方塊。 如需有關加入 Web 參考的詳細資訊，請參閱 <<c0> [ 使用 Visual Studio](../core/using-visual-studio.md)。  
  
  如果想使用「商務程序執行語言」(Business Process Execution Language，BPEL) 匯出程序匯出您的協調流程，您不能參考現有 BizTalk 專案中的 Web 參考。 如果您參考現有 BizTalk 專案中的 Web 參考，則 BPEL 匯出程序會自動產生第二個 WSDL 檔案，而您則會失去您的繫結資訊。  
  
## <a name="see-also"></a>另請參閱  
 [建立 Web 連接埠](../core/creating-web-ports.md)   
 [使用 Web 服務](../core/consuming-web-services.md)