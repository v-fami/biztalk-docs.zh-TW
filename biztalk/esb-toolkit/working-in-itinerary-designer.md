---
title: 在路線設計工具中工作 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06742cb8-f6d6-46e2-adc0-6be9a3d6a447
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baf474c68d91b7648f7f0efcfe4e85e7531e4aa1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976780"
---
# <a name="working-in-itinerary-designer"></a>在路線設計工具中工作
建立 Microsoft Visual C# 專案之後，您可以建立新的路線模型並加入專案中現有的行程。 下列步驟說明如何建立新的行程、 加入現有的路線模型，或變更行程的名稱。  
  
> [!NOTE]
>  之前使用路線設計工具，您必須安裝 Microsoft.Practices.ESB.CORE Windows Installer （.msi 檔案） 從[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]安裝資料夾。 這個步驟會將必要的執行階段組件安裝至全域組件快取。  
  
## <a name="basic-operations"></a>基本作業  

#### <a name="create-an-itinerary"></a>建立行程  
  
1.  在 方案總管 中，以滑鼠右鍵按一下 C# 專案名稱，指向**新增**，然後按一下 **新的行程**。  
  
2.  在**名稱**方塊底部的對話方塊中，輸入行程的名稱，然後按一下**新增**。  
  
    > [!NOTE]
    >  建立新的行程並顯示在路線設計工具，並建立對應的.itinerary 檔並將其顯示在 [方案總管] 中。  
  
#### <a name="add-an-existing-itinerary-to-the-project"></a>將現有的行程加入專案
  
1.  在 方案總管 中，以滑鼠右鍵按一下 C# 專案名稱，指向**新增**，然後按一下 **現有項目**。  
  
2.  在**加入現有項目**對話方塊中，巡覽至包含路線，依序按一下目錄路線，然後**新增**。  
  
    > [!NOTE]
    >  路線會加入至專案。  
  
#### <a name="change-the-name-of-an-itinerary"></a>變更行程的名稱  
  
1.  在 方案總管中以滑鼠右鍵按一下您想要重新命名，然後按一下 .itinerary 檔案**重新命名**。  
  
2.  輸入新的檔案名稱，然後按 ENTER 鍵。  
  
#### <a name="save-an-itinerary"></a>儲存路線  
  
在**檔案**功能表上，按一下 **儲存\<路線名稱\>**。  
  
> [!NOTE]
>  路線檔案會儲存為 DSL 模型中對應的 XML 格式。  
  
#### <a name="set-itinerary-export-properties"></a>設定路線匯出屬性  
  
1.  在 [屬性] 視窗中，輸入**名稱**屬性。  
  
2.  在 [屬性] 視窗中，輸入**版本**屬性。  
  
3.  在 [屬性] 視窗中，指定**為要求回應**使用下拉式清單的屬性。 將此屬性設定為**true**如果[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]上手與通訊的用戶端應用程式使用要求-回應訊息交換模式。  
  
4.  在 [屬性] 視窗中，設定**匯出模式**屬性**預設**或**Strict**。  
  
    > [!NOTE]
    >  建立時[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]使用路線設計工具的行程**匯出模式**屬性可以用來定義服務將會執行位置。 設定**匯出模式**屬性**Strict**可確保路線服務會執行其規定的容器中; 在此情況下，XML 行程中的每個路線服務的階段內容，指定服務執行所在的管線。 如果這個屬性設定為**預設**、 與 Microsoft ESB 行程即會建立具有指定，任何階段和規定的順序，但不是一定需要的管線階段中執行路線服務。  
  
#### <a name="export-an-itinerary-to-a-file"></a>匯出至檔案的行程  
  
1.  在 [屬性] 視窗中，按一下**XML 路線匯出工具**中**模型匯出工具**下拉式清單。  
  
2.  在 [屬性] 視窗中，設定**路線 XML 檔案**屬性設為新值。  
  
#### <a name="export-an-itinerary-to-a-database"></a>匯出到資料庫的行程  
  
1.  在 [屬性] 視窗中，按一下**資料庫路線匯出工具**中**模型匯出工具**下拉式清單。  
  
2.  在 [屬性] 視窗中，設定**路線資料庫**屬性指向路線資料庫的連接字串。  
  
3.  在 [屬性] 視窗中，設定**路線狀態**屬性**發佈**或**部署**。  
  
    > [!NOTE]
    >  行程匯出至資料庫時**路線狀態**設**已發佈**、 計劃將會生效的[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]之後屬性設定為執行之前的時間**部署**。  
  
## <a name="security-operations"></a>安全性作業  
 藉由使用路線設計工具，您可以保護機密資訊，例如密碼和其他認證儲存在[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線，方法是加密此資訊會使用 X.509 憑證。  
  
#### <a name="select-the-x509-certificate-for-an-itinerary"></a>選取路線的 X.509 憑證  
  
1.  在路線設計工具屬性] 視窗中，展開 [**加密憑證**屬性，，然後按一下**存放區位置**下拉式清單並選取**CurrentUser**或**LocalMachine**。 這將 X.509 憑證存放區與目前的使用者或本機電腦產生關聯。  
  
2.  在 [屬性] 視窗中，按一下**存放名稱**下拉式清單並選取其對應至您的憑證存放區的值。  
  
3.  在 [屬性] 視窗中，按一下 [加密憑證屬性旁邊的省略符號按鈕 （...），然後選取**X.509 憑證**中**選取憑證**] 對話方塊。  
  
#### <a name="remove-the-x509-certificate-from-an-itinerary"></a>移除路線的 X.509 憑證  
  
-   在路線設計工具屬性] 視窗中，展開 [**加密憑證**屬性，並將其設定**存放區位置**屬性設為不同的值。 這會解除關聯的舊憑證[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線的模型。  
  
#### <a name="disable-the-x509-certificate-validation"></a>停用的 X.509 憑證驗證  
  
在 登錄編輯器中，移至子機碼**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk ESB Toolkit\2.0\Designer**，然後設定**RequireX509Certificate**屬性值設定為**false**。  
  
> [!NOTE]
>  如果您已安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]子機碼是在支援 64 位元作業系統上**HKEY_LOCAL_MACHINE\SOFTWARE\SysWOW64\Microsoft\BizTalk ESB Toolkit\2.0\Designer**。