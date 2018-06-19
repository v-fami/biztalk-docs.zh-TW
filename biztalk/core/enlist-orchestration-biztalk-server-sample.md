---
title: 登錄協調流程 （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- orchestrations, enlisting
- examples, orchestrations
ms.assetid: d8d53e59-2313-40dd-a278-0a29d8eb4ce8
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e8d85a49b410f0571e8e9cb0be816f1feda139e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968860"
---
# <a name="enlist-orchestration-biztalk-server-sample"></a>登錄協調流程 （BizTalk Server 範例）
「登錄協調流程」範例會示範如何向主控件登錄 BizTalk Server 協調流程。  
  
> [!WARNING]
>  如果在部署後不需要部署指令碼，就應該將其移除。 必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例包括存取 Windows Management Instrumentation (WMI) 物件模型中，Visual Basic Scripting Edition (VBScript) 版本和 Visual C# 版本會存取**System.Management**所提供的物件.NET Framework。 這兩個版本最後都會存取 BizTalk Server WMI 提供者來執行下列作業：  
  
-   在指定協調流程名稱和組件名稱的情形下，查詢已部署的特定 BizTalk Server 協調流程。  
  
-   向預設主控件登錄該協調流程。  
  
-   處理任何錯誤，讓有意義的資訊能傳回給使用者。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 範例位於下列 SDK 位置：  
  
-   VBScript 版： \<*範例路徑*\>\Admin\WMI\Enlist Orchestration\VBScript\  
  
-   Visual C# 版本： \<*範例路徑*\>\Admin\WMI\Enlist Orchestration\CSharp\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|在 \VBScript 資料夾中：<br /><br /> EnlistOrch.vbs|VBScript 檔案，它會接受特定參數來指定要向主控件登錄的協調流程。|  
|在 \CSharp 資料夾中：<br /><br /> App.ico、AssemblyInfo.cs、BTSampleEnlistOrc.csproj、BTSampleEnlistOrc.sln、EnlistOrc.cs|專案、方案和原始程式檔，用於建置 Visual C# 命令列應用程式，這個應用程式會接受特定參數來指定要向主控件登錄的協調流程。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 VBScript 版的「登錄協調流程」範例是由單一 Visual Basic 指令碼檔案所組成，您不需要建置或初始化該檔案。  
  
#### <a name="to-build-the-visual-c-version-of-the-enlist-orchestration-sample"></a>若要建置 Visual C# 版的登錄協調流程範例  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟方案檔 BTSampleEnlistOrc.sln。  
  
2.  在**建置**功能表上，按一下 **建置方案**。  
  
#### <a name="to-run-the-enlist-orchestration-sample"></a>若要執行登錄協調流程範例  
  
1.  在命令視窗中，根據您打算執行此範例的 VBScript 版或 Visual C# 版，分別瀏覽至下列其中一個資料夾：  
  
     \<*範例路徑*\>\Admin\WMI\Enlist Orchestration\VBScript\  
  
     \<*範例路徑*\>AdminWMIEnlist OrchestrationCSharpbinDebug  
  
2.  根據您打算執行此範例的 VBScript 版或 Visual C# 版，分別使用 cscript 程式執行 EnlistOrch.vbs 檔，或是執行 EnlistOrc.exe 檔。 無論執行哪個版本，都會傳遞下列命令列引數：  
  
    -   **\<** ***OrchestrationName* \>。** 要登錄的協調流程名稱。  
  
    -   **\<** ***AssemblyName* \>。** 協調流程已部署於其中的組件名稱。 如果組件名稱包含空格，請用引號括住該名稱。  
  
         例如: (VBScript):  
  
        ```  
        cscript EnlistOrch.vbs MyBusinessOrchestration "My Business Assembly"  
        ```  
  
         -或- (Visual C#)：  
  
        ```  
        EnlistOrc MyBusinessOrchestration "My Business Assembly"  
        ```  
  
## <a name="comments"></a>註解  
 您可以在執行的所有工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，也可以執行使用存取 Windows WMI 物件模型的指令碼和使用 Visual C# 存取**System.Management**提供物件.NET framework。  
  
 指令檔 EnlistOrch.vbs 和 Visual C# 來源檔 EnlistOrc.cs，包含了詳細註解，以及這兩個檔案所執行作業的相關進一步說明。 如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。  
  
## <a name="see-also"></a>請參閱  
 [Admin-WMI (BizTalk Server Samples 資料夾)](../core/admin-wmi-biztalk-server-samples-folder.md)