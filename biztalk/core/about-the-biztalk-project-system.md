---
title: 關於 BizTalk 專案系統 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects, about projects
- applications, creating
- creating, applications
- creating, business solutions
- business solutions, creating
ms.assetid: 69807e57-356e-451d-b803-4253b891b617
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43bfc47725defe70c11d0d839fb7985b91403c91
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019885"
---
# <a name="about-the-biztalk-project-system"></a>關於 BizTalk 專案系統
您可以使用 BizTalk 專案系統以建立部分或所有的 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式或商務方案。 任何這類方案的核心項目為 BizTalk 專案—為部署之前建置和產生至組件的結構描述、協調流程、Web 訊息類型、類別、管線、對應和參考等項目的集合。  
  
 較簡單的商務方案可包含產生至單一組件的單一 BizTalk 專案。 如果您的商務解決方案是更複雜 — 比方說，您有許多不同系統和程序整合的解決方案，可能的 BizTalk 方案或許具有許多組件產生的 BizTalk 專案，並部署到數個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦。  
  
> [!IMPORTANT]
>  您無法在組件名稱中使用逗號。  
  
 當您建立 BizTalk 專案時，一般會包含下列清單中的一或多個檔案類型。 這些檔案類型在建立方案時扮演特定角色，而 BizTalk 專案系統會為每一種檔案類型提供對應的圖形化設計工具。  
  
- **協調流程。** 協調流程代表商務程序的工作流程。 您可以使用「協調流程設計師」設計協調流程。 如需協調流程設計工具的詳細資訊，請參閱[協調流程使用協調流程設計師建立](../core/creating-orchestrations-using-orchestration-designer.md)。  
  
- **結構描述。** 結構描述描述 XML 文件的結構。 結構描述會在組織中的應用程式之間或交易夥伴之間交換資訊。 BizTalk 編輯器可簡化定義結構描述的程序。 如需 「 BizTalk 編輯器的詳細資訊，請參閱 <<c0> [ 建立結構描述使用 BizTalk 編輯器](../core/creating-schemas-using-biztalk-editor.md)。  
  
- **對應。** 對應會將資料從一種格式轉換為另一種格式。 BizTalk 對應工具會以並排方式呈現來源結構描述和目的結構描述，讓您定義不同訊息的資料項目之間的轉換。 如需有關 BizTalk 對應工具的詳細資訊，請參閱[建立的對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。  
  
- **管線。** 管線會執行各種作業，為進一步處理內送或外寄訊息做準備。 「管線設計師」可讓您實作如加密與解密、壓縮、重新格式化以及驗證等作業。 如需有關管線設計工具的詳細資訊，請參閱[管線使用管線設計師建立](../core/creating-pipelines-using-pipeline-designer.md)。  
  
  BizTalk 專案與 Team Foundation Server (TFS) 相容。 如需有關設計的詳細資訊，請開發和部署 BizTalk Server 中的解決方案內搭配 TFS，請參閱[開發整合解決方案使用 BizTalk Server 和 Team Foundation Server](http://www.microsoft.com/downloads/details.aspx?FamilyID=ed7bd0ee-1385-4041-8f2a-354594ee88f3&DisplayLang=en)。  
  
> [!IMPORTANT]
>  TFS 建置會顯示一個名稱為「MSBuild 平台」的屬性，其中可以有 3 個值：「自動」、「x86」及「x64」。 為確保建置成功完成，以上屬性的值必須設定為 x86。  
  
 BizTalk 專案可與 Visual Studio 中的其他專案並存。 如同 Visual Studio 中的所有專案系統，BizTalk 專案可包含其他檔案，例如 ASP.NET 頁面，而且可以參考您已建立的其他專案和組件。 如需有關 BizTalk 專案範本的詳細資訊，請參閱[BizTalk Server 專案範本](../core/biztalk-server-project-templates.md)。 如需建立 BizTalk 專案的詳細資訊，請參閱[如何建立 BizTalk 專案](../core/how-to-create-biztalk-projects.md)。  
  
> [!WARNING]
>  雖然您可以從可在 Visual Studio 中使用的其他專案系統來存取 BizTalk 設計工具，不過它們的行為無法預測。 請只在 BizTalk 專案的環境中使用「協調流程設計師」、「管線設計師」、「BizTalk 編輯器」和「BizTalk 對應工具」。  
  
## <a name="see-also"></a>另請參閱  
 [使用協調流程設計師建立協調流程](../core/creating-orchestrations-using-orchestration-designer.md)   
 [使用 BizTalk 編輯器建立結構描述](../core/creating-schemas-using-biztalk-editor.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)   
 [使用管線設計師建立管線](../core/creating-pipelines-using-pipeline-designer.md)   
 [開發人員工具](../core/developer-tools.md)