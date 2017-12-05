---
title: "列舉接收位置 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, examples
- receive locations, enumerating
- examples, receive locations
ms.assetid: 27ff8ac6-7e8e-4dde-84d1-d21bf417ddd7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82fcdc400395d7bbfd6de8f9bc0fca85114a25dc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="enumerate-receive-locations-biztalk-server-sample"></a>列舉接收位置 （BizTalk Server 範例）
「列舉接收位置」範例會示範如何擷取一或多個接收位置的詳細資訊。  
  
> [!WARNING]
>  如果在部署後不需要部署指令碼，就應該將其移除。 必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例包括存取 Windows WMI 物件模型中，Visual Basic Scripting Edition (VBScript) 版本和 Visual C# 版本會存取**System.Management** .NET Framework 所提供的物件。 這兩個版本最後都會存取 BizTalk Server WMI 提供者來執行下列作業：  
  
-   查詢設定的接收位置或特定接收位置，指定其名稱。  
  
-   截取和顯示每個相關接收位置的詳細資訊。  
  
-   處理任何錯誤，讓有意義的資訊能傳回給使用者。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 範例位於下列 SDK 位置：  
  
-   VBScript 版： \<*範例路徑*\>\Admin\WMI\Enumerate Receive Locations\VBScript\  
  
-   Visual C# 版本： \<*範例路徑*\>\Admin\WMI\Enumerate Receive Locations\CSharp\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|在 \VBScript 資料夾中：<br /><br /> EnumRecLocs.vbs|VBScript 檔，該檔案會擷取所有與設定的接收位置相關的詳細資訊。|  
|在 \CSharp 資料夾中：<br /><br /> App.ico、AssemblyInfo.cs、BTSampleEnumerateRLs.csproj、BTSampleEnumerateRLs.sln、EnumRLs.cs|專案、解決方案和來源檔，用於建置 Visual C# 命令列應用程式，以擷取所有設定接收位置或特定接收位置的詳細資訊。|  
  
## <a name="building-and-initializing-this-sample"></a>建置和初始化此範例  
 VBScript 版的「列舉接收位置」範例是由單一 Visual Basic 指令碼檔案所組成，您不需要建置或初始化該檔案。  
  
#### <a name="to-build-the-visual-c-version-of-the-enumerate-receive-locations-sample"></a>建置 Visual C# 版的列舉接收位置範例  
  
1.  在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟方案檔 BTSampleEnumerateRLs.sln。  
  
2.  在**建置**功能表上，按一下 **建置方案**。  
  
## <a name="running-this-sample"></a>執行此範例  
  
#### <a name="to-run-the-enumerate-receive-locations-sample"></a>執行列舉接收位置範例  
  
1.  在命令視窗中，根據您要執行的是此範例的 VBScript 版或 Visual C# 版而定，分別瀏覽至下列其中一個資料夾：  
  
     \<*範例路徑*\>\Admin\WMI\Enumerate 接收 Locations\VBScript\  
  
     \<*範例路徑*\>\Admin\WMI\Enumerate 接收 Locations\CSharp\bin\Debug\  
  
2.  根據您要執行的是此範例的 VBScript 版或 Visual C# 版而定，分別使用 cscript 程式執行 EnumRecLocs.vbs 檔，或是執行 EnumRl.exe 檔。 針對 Visual C# 版本，傳遞下列兩個命令列引數的其中一個：  
  
    -   **\<ReceiveLocationName\>。** 要顯示其詳細資訊的接收位置名稱。 如果接收位置名稱包含空格，請用引號括住該名稱。  
  
    -   **/?.** 顯示說明。  
  
         例如 (VBScript)：  
  
        ```  
        cscript EnumRecLocs.vbs  
        ```  
  
         -或- (Visual C#)：  
  
        ```  
        EnumRl "My Receive Location #3"  
        ```  
  
         -或- (Visual C#)：  
  
        ```  
        EnumRl /?  
        ```  
  
    > [!NOTE]
    >  此範例的 VBScript 版不接受任何命令列參數，因此只能擷取和顯示所有設定接收位置的詳細資訊。  
  
## <a name="comments"></a>註解  
 您可以在執行的所有工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，也可以執行使用存取 Windows WMI 物件模型的指令碼和使用 Visual C# 存取**System.Management**提供物件.NET framework。  
  
 指令碼檔案 EnumRecLocs.vbs 和 Visual C# 來源檔 EnumRLs.cs 包含詳細註解，以及有關這兩個檔案所執行作業的進一步說明。 如需詳細資訊，請參閱 < 在 Windows Management Instrumentation [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102)。  
  
## <a name="see-also"></a>請參閱  
 [Admin-WMI (BizTalk Server Samples 資料夾)](../core/admin-wmi-biztalk-server-samples-folder.md)