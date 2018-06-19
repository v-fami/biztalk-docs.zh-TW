---
title: 解除部署配接器使用 WCF LOB 配接器 SDK |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98f9a124-9e63-4451-af0e-ffee752fbeac
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1332e41593ede5f7075ec7f5ede1293d79d65594
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963564"
---
# <a name="undeploy-an-adapter-using-the-wcf-lob-adapter-sdk"></a>解除部署配接器使用 WCF LOB 配接器 SDK
若要解除部署配接器從電腦時，使用者必須執行下列兩項工作：  
  
1.  從全域組件快取 (GAC)，解除安裝配接器組件 （和任何相依組件）。  
  
2.  在 machine.config 檔案中移除的配接器繫結和配接器繫結項目。  
  
## <a name="uninstall-an-assembly-from-the-gac"></a>從 GAC 解除安裝組件  
  
#### <a name="use-the-windows-interface"></a>使用 Windows 介面  
  
1.  開啟 Windows 檔案總管，如下所示： 按一下**啟動**，指向**所有程式**，指向 **附屬應用程式**，然後按一下  **Windows 檔案總管**.  
  
2.  瀏覽至 GAC，位於 systemdrive%\Windows\Assembly。  
  
3.  以滑鼠右鍵按一下包含您的應用程式在每個組件檔案中，按一下**解除安裝**，然後按一下 **是**確認。  
  
#### <a name="use-the-command-line"></a>使用命令列  
  
1.  開啟[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]命令提示字元。  
  
2.  在命令提示字元中，輸入下列命令：  
  
     **gacutil /u** \<*完整**組件名稱*\>  
  
     這個命令中，組件名稱會是要從 GAC 解除安裝組件的名稱。  
  
     下列範例會從 GAC 中移除名為 hello.dll 的組件。  
  
     `gacutil /u "MyAdapter,Version=1.0.0.0, Culture=neutral, PublicKeyToken=fafafafafafafafa"`
  
## <a name="remove-the-adapter-binding-from-the-machineconfig-file"></a>移除 Machine.config 檔案中的配接器繫結  
 您可以手動編輯 machine.config 檔移除配接器繫結，或使用 服務組態編輯器。 此區段會列出這兩個步驟。 
  
#### <a name="manually-edit-the-machineconfig-file"></a>手動編輯 machine.config 檔  
  
1.  編輯位於 Microsoft .NET 組態資料夾中的 machine.config 檔。 若要這樣做，請按一下**啟動**，按一下 **執行**，型別**記事本\<Windows 安裝路徑\>\Microsoft.NET\Framework\\< 版本\>\CONFIG\machine.config**，然後按一下 **確定**。  
  
    > [!NOTE]
    >  讓 machine.config 檔案的備份，才能變更防範編輯的錯誤。  
  
2.  更新 machine.config 檔案。 尋找您想要移除介面卡的 bindingExtensions 項目。 根據存在的其他資訊，執行下列其中一項：  
  
    -   如果有其他 bindingExtensions，移除只有您的配接器擴充功能。  
  
    -   如果有任何其他 bindingExtensions，您可以移除 bindingExtensions 區段 （包括您的配接器擴充功能）。  
  
    -   如果沒有其他 bindingExtensions 或擴充功能，您可以移除延伸模組 > 一節。  
  
    -   最後，如果 system.serviceModel 包含只有您的配接器擴充功能，您可以移除整個 system.serviceModel > 一節。  
  
3.  重複步驟 2 bindingElementExtensions 項目。  
  
4.  關閉並儲存 machine.config 檔案。  
  
#### <a name="use-the-service-configuration-editor-do-change-the-machineconfig-file"></a>使用 服務組態編輯器就會變更 machine.config 檔案  
  
1.  開啟 [服務組態編輯器]。 請參閱[服務組態編輯器](https://msdn.microsoft.com/library/ms732009.aspx)如需詳細資訊。
  
2.  在樹狀檢視窗格中 (標示為**組態**)，展開節點樹狀目錄。 按一下**進階**資料夾中，按一下 **延伸**資料夾，然後再選取繫結延伸項目。  
  
3.  在繫結擴充編輯器的詳細資料窗格中，按一下您想要刪除，然後按一下 繫結延伸**刪除**。 在下圖中，MyAdapterExtension 會反白顯示，並將被刪除。  
  
     ![具有新增之延伸的服務組態編輯器。] (../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/955d37ea-cba5-49db-90de-0f8feb49c0e0.gif "955d37ea-cba5-49db-90de-0f8feb49c0e0")  
  
4.  關閉 [服務組態編輯器]。  
  
## <a name="see-also"></a>請參閱  
 [部署配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)