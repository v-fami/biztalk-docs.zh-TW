---
title: "加入專案項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, orchestrations
- projects, schemas
- projects, files
- projects, pipelines
- projects, maps
ms.assetid: d1b922d5-8ece-4e1a-a390-e6ae1222665a
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfb6aaa0a00488c1181d440e0ce7e5777ef4477d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-project-items"></a>加入專案項目
在 BizTalk 專案系統的內容中，專案項目是設定的項目 (例如對應或結構描述)。 BizTalk 應用程式包含一或多個協調流程、結構描述、對應及管線。  
  
> [!NOTE]
>  當您將項目新增至專案時，因為句號是 .NET 命名空間的分隔符號，所以請不要在名稱中使用句號 (.)。 如果您在項目名稱中使用句號，則項目的類型名稱會包含底線 (_)，而非句號。  
  
> [!NOTE]
>  當將結構描述、 對應或管線新增到資料夾，**完整格式名稱**屬性會自動產生，並包含命名空間和類型。  
  
## <a name="orchestrations"></a>協調流程  
 協調流程是一種以 XLANG/s 語言表示商務程序的方法。 XLANG/s 是 Microsoft [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] 所引進且以 XML 為基礎之語言 (XLANG) 的更新版本。 XLANG/s 可用來補充現有程序性語言的不足，例如 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] 與 Microsoft [!INCLUDE[btsVBNet](../includes/btsvbnet-md.md)]。  
  
 您可以使用協調流程設計師來建立您要併入 BizTalk 專案的協調流程。 所有您在協調流程設計師中所建立的協調流程都會以 .odx 為副檔名。  
  
## <a name="schemas"></a>結構描述  
 結構描述是文件或訊息之結構的定義。 因為結構描述是與結構內的記錄和欄位相關，所以會包含屬性資訊。 在適當的情況下，結構描述可以包含多個子結構描述。  
  
 您可以使用 BizTalk 編輯器來匯入、編輯或建立結構描述。 接著，您可以使用您建立的結構描述在 BizTalk 對應工具中產生對應。 所有您使用 BizTalk 編輯器儲存的結構描述都是以 .xsd 為副檔名。  
  
 如需結構描述和 BizTalk 編輯器的詳細資訊，請參閱[建立結構描述使用 BizTalk 編輯器](../core/creating-schemas-using-biztalk-editor.md)。  
  
## <a name="maps"></a>地圖  
 對應是一種 XML 檔案，負責定義不同結構描述中之記錄與欄位間的對應。 您可根據產業標準、非產業標準 (例如內部標準或已知問題) 或現有檔案來建立對應。 當您想要將接收或傳送的資料從某種格式轉換成另一種格式時，就要建立對應。 您可以使用 BizTalk 對應工具來建立您要併入 BizTalk 專案的對應。 所有您在 BizTalk 對應工具中儲存的對應都是以 .btm 為副檔名。 如需 BizTalk 對應工具的詳細資訊，請參閱[建立對應使用 BizTalk 對應工具](../core/creating-maps-using-biztalk-mapper.md)。  
  
## <a name="pipelines"></a>管線  
 您可以使用「管線設計師」來建立傳送管線和接收管線。 管線是一種軟體基礎結構，可定義和連結處理 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所接收或傳送之訊息的一或多個階段。 管線會以特定的順序實作這些階段，並包含諸如編碼或解碼、組譯或反組譯以及加密或解密等函式。  
  
 BizTalk 專案中所包含的預設管線參考只能處理 XML 文件。 如果您想要處理一般檔案、EDI 文件或其他檔案類型，則必須適當地建立新的管線。 所有使用管線設計師所建立的管線都是以 .btp 為副檔名。 如需管線和管線設計師 」 的詳細資訊，請參閱[管線使用管線設計師建立](../core/creating-pipelines-using-pipeline-designer.md)。  
  
## <a name="valid-files-for-biztalk-projects"></a>BizTalk 專案的有效檔案  
 當您搭配使用 BizTalk 專案時，您可以包含許多不同的檔案 (例如 HTML 檔案、XML 檔案、接收管線檔案和結構描述檔案)。 在發行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 之前，當您將 BizTalk 專案建立到組件中，只有下列檔案類型才會包含在組件中：協調流程、結構描述、對應和管線。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 版本中，組件可以包含 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建置系統所支援的任何物件。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 專案](../core/working-with-biztalk-projects.md)