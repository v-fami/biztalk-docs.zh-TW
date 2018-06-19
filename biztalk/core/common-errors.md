---
title: 常見的錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4fe48a8e-def0-4a00-aa7f-9a49ae555351
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b882c44e69489114a2dd8084df71d6414df0cb5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971532"
---
# <a name="common-errors"></a>一般錯誤
本主題列出使用 BizTalk 對應工具建立對應時可能會遇到的常見錯誤訊息。  
  
## <a name="you-receive-error-event-id-324-when-parsing-dates"></a>您在剖析日期時接收到錯誤事件識別碼 324。  
  
### <a name="problem"></a>問題  
 當您使用資料庫**值擷取程式 」** 運算質擷取日期欄位，您的文件引導模式中可能會針對輸出文件定義的驗證失敗。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能會記錄事件記錄檔中的驗證錯誤，如下所示：  
  
 事件來源： BizTalk Server  
  
 事件類別目錄： 文件處理  
  
 事件識別碼： 324  
  
 描述：  
  
 BizTalk Server 發生錯誤。  
  
 詳細資料：  
  
 -----------------------------\-  
  
 XML 文件驗證因下列原因失敗： 錯誤剖析 '10/12/1995年' 為日期資料類型。  
  
 訊息擱置的佇列識別碼:"{A1127909-CA36-4359-B672-7CBA8B60BDAF}"  
  
### <a name="cause"></a>原因  
 日期格式 (由資料來源所傳回的格式) 不是 XML 所需要的 ISO 8601 格式。  
  
### <a name="resolution"></a>解決方案  
 若要解決這個問題，請執行下列其中一個動作：  
  
-   編輯您的輸出文件定義以使用字串資料型別而非日期資料型別。  
  
-   建立自訂[!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsVBNoVersion](../includes/btsvbnoversion-md.md)]**指令碼**將資料庫的輸出轉換的運算質**值擷取程式 」** 成 ISO 8601 格式的運算質。  
  
 如需詳細資訊，請參閱知識庫文章[278737](http://support.microsoft.com/kb/278737/en-us)。  
  
## <a name="you-receive-internal-compiler-error-0xc0000005-at-address-53624fd6-when-compiling-the-maps"></a>您在編譯對應時收到編譯器內部錯誤 (0xc0000005 於位址 53624FD6)  
  
### <a name="problem"></a>問題  
 當您編譯由大型結構描述、對應或協調流程所構成的單一 BizTalk 專案時，編譯器可能會產生如下錯誤：  
  
 編譯器內部錯誤 (0xc0000005 於位址 53624FD6): 可能的原因，是 'CODEGEN'。  
  
### <a name="cause"></a>原因  
 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 編譯器在單一專案中，所有字串總大小的限制為 16 MB。 在編譯 BizTalk 專案時，編譯器會序列化結構描述、對應和協調流程以建立組件，這樣便會增加所有字串的總大小，進而可能超過限制。  
  
### <a name="resolution"></a>解決方案  
 若要解決這個問題，您可以將結構描述或對應分散到不同的 BizTalk 專案中。  
  
## <a name="you-receive-errors-about-the-type-name-of-a-biztalk-artifact"></a>您收到關於 BizTalk 成品類型名稱的錯誤訊息  
  
### <a name="problem"></a>問題  
 在 BizTalk 專案中，建立對應以檔名**System.btm**或**Microsoft.btm**。 當您建置專案時，BizTalk 對應工具產生類似下列任一項的錯誤：  
  
-   「類型名稱 'SerializableAttribute' 不存在...」  
  
-   「類型名稱 'NonSerializableAttribute' 不存在...」  
  
-   「類型名稱 'SerializableAttributeAttribute' 不存在...」  
  
-   「類型名稱 'XLANs' 不存在...」  
  
### <a name="cause"></a>原因  
 **型別名稱**中**屬性**方格不應有任何保留的.NET 命名空間，例如**系統**， **Microsoft**等等。  
  
### <a name="resolution"></a>解決方案  
 若要解決此問題，您可以使用下列任一個因應措施：  
  
-   將對應的名稱修改成任一個非 .NET 保留字的字串。 根據預設，BizTalk 專案系統會建立**型別名稱**個別成品的名稱。  
  
     針對如： 名稱建立新的對應**Map1.btm**設定**型別名稱**屬性值設定為**Map1**。 不過，重新命名現有的 BizTalk 成品不會變更**型別名稱**。  
  
-   確認 BizTalk 專案中所有成品的檔案名稱均不是保留的 .NET 命名空間。  
  
## <a name="you-receive-errors-about-the-file-name-of-a-biztalk-artifact"></a>您收到關於 BizTalk 成品檔案名稱的錯誤訊息  
  
### <a name="problem"></a>問題  
 當您欠至 BizTalk 專案時，BizTalk 對應工具產生類似下列任一項的錯誤：  
  
-   「 檔案\<filename\>有重複的命名空間和類型名稱屬性的值。 」  
  
-   "命名空間\<名稱\>已經包含 '_' 的定義。 」  
  
### <a name="cause"></a>原因  
 在 BizTalk 專案中，檢查下列各項：  
  
-   是否有多個成品具有相同的檔案名稱。 如例如**Map1.xsd**和**Map1.btm**。  
  
-   檔案名稱包含特殊字元只 (**~**， **！**，  **@** 等。)。  
  
### <a name="resolution"></a>解決方案  
 若要解決此問題，您可以使用下列任一個因應措施：  
  
-   重新命名檔案。 確認 BizTalk 專案中所有成品的檔案名稱都是唯一的。  
  
-   確認 BizTalk 專案中所有成品的類型名稱都是唯一的。  
  
## <a name="building-any-c-workflow-project-with-biztalk-mapper-shows-a-warning-regarding-version-conflict-for-envdtedll"></a>使用 BizTalk 對應工具建置任何 C# 工作流程專案時，會顯示關於 EnvDTE.dll 版本衝突的警告  
  
### <a name="problem"></a>問題  
 使用 BizTalk 對應工具建置任何 C# 工作流程專案時，一律會顯示下列關於 EnvDTE.dll 版本衝突的警告。  
  
 沒有辦法解決 "EnvDTE，版本=8.0.0.0，文化特性=非語言相關，PublicKeyToken=b03f5f7f11d50a3a" 和 "EnvDTE，版本=7.0.3300.0，文化特性=非語言相關，PublicKeyToken=b03f5f7f11d50a3a" 之間的衝突。 選擇"EnvDTE，版本 = 8.0.0.0，Culture = neutral，PublicKeyToken = b03f5f7f11d50a3a"任意。  App.config 重新對應組件，請考慮"EnvDTE，Culture = neutral，PublicKeyToken = b03f5f7f11d50a3a"從版本"7.0.3300.0"[] 版本 」 8.0.0.0"[C:\Program Files (x86) \Microsoft Visual Studio 10.0\Common7\IDE\PublicAssemblies\EnvDTE.dll]若要解決衝突，並移除警告。 C:\Windows\Microsoft.NET\Framework\v4.0.30319\Microsoft.Common.targets(1360,9)： 警告 MSB3247： 同一個相依組件的不同版本之間發現衝突。  
  
 WorkflowConsoleApplication3]-> [C:\Users\btslabs\Desktop\WorkflowConsoleApplication3\bin\Debug\WorkflowConsoleApplication3.exe  
  
### <a name="cause"></a>原因  
 這是因為 Microsoft.BizTalk.Mapper.OM.dll 即在參考對應工具活動。  
  
### <a name="resolution"></a>解決方案  
 忽略此警告。  
  
## <a name="see-also"></a>請參閱  
 [地圖疑難排解](../core/troubleshooting-maps.md)