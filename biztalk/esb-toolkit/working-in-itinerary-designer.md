---
title: 使用路線設計工具 |Microsoft Docs
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
ms.openlocfilehash: 747ce8a750f2b2c775deaa1123a1b6b1d387eafc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999399"
---
# <a name="working-in-itinerary-designer"></a>使用路線設計工具
建立 Microsoft Visual C# 專案之後，您可以建立新的路線模型，並加入專案中現有的路線。 下列步驟說明如何建立新的路線、 加入現有的路線模型，或變更路線的名稱。  
  
> [!NOTE]
>  之前使用路線設計工具，您必須安裝 Microsoft.Practices.ESB.CORE Windows Installer （.msi 檔案） 從[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]安裝資料夾。 此步驟會安裝必要的執行階段組件至全域組件快取。  
  
## <a name="basic-operations"></a>基本作業  

#### <a name="create-an-itinerary"></a>建立路線  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 C# 專案名稱，指向**新增**，然後按一下**新路線**。  
  
2.  在 **名稱**方塊底部的  對話方塊中，輸入路線，名稱，然後按一下**新增**。  
  
    > [!NOTE]
    >  建立並顯示在路線設計工具中，新的路線，並建立對應的.itinerary 檔並將其顯示在 [方案總管] 中。  
  
#### <a name="add-an-existing-itinerary-to-the-project"></a>加入專案中的現有路線
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 C# 專案名稱，指向**新增**，然後按一下**現有項目**。  
  
2.  在 **加入現有項目** 對話方塊中，瀏覽至目錄，其中包含路線，按一下 路線，然後**新增**。  
  
    > [!NOTE]
    >  以路線為加入至專案。  
  
#### <a name="change-the-name-of-an-itinerary"></a>路線的名稱變更  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下您想要重新命名，然後按一下.itinerary 檔案**重新命名**。  
  
2.  輸入新的檔案名稱，然後按 ENTER 鍵。  
  
#### <a name="save-an-itinerary"></a>儲存路線  
  
在 **檔案**功能表上，按一下**儲存\<路線名稱\>**。  
  
> [!NOTE]
>  路線的檔案會儲存為 DSL 模型中對應的 XML 格式。  
  
#### <a name="set-itinerary-export-properties"></a>設定路線的匯出屬性  
  
1. 在 [屬性] 視窗中，輸入**名稱**屬性。  
  
2. 在 [屬性] 視窗中，輸入**版本**屬性。  
  
3. 在 [屬性] 視窗中，指定**是要求回應**使用下拉式清單的屬性。 將此屬性設定為**真**如果[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]匝道與通訊的用戶端應用程式使用要求-回應訊息交換模式。  
  
4. 在 [屬性] 視窗中，設定**匯出模式**屬性設**預設**或是**Strict**。  
  
   > [!NOTE]
   >  建立時[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]使用路線設計工具的路線**匯出模式**屬性可用來定義服務執行的位置。 設定**匯出模式**屬性設**Strict**確保路線服務會在其指定的容器中執行; 在此情況下，XML 路線中的每個路線服務有階段屬性，指定服務執行所在的管線。 如果這個屬性設定為**預設**、 建立相容於 Microsoft ESB 路線，使用指定的任何階段和路線服務執行規定的順序，但不是一定是所需的管線階段中。  
  
#### <a name="export-an-itinerary-to-a-file"></a>匯出至檔案的路線  
  
1.  在 [屬性] 視窗中，按一下**XML 路線匯出工具**中**模型匯出工具**下拉式清單。  
  
2.  在 [屬性] 視窗中，設定**路線 XML 檔案**屬性設為新值。  
  
#### <a name="export-an-itinerary-to-a-database"></a>匯出到資料庫的路線  
  
1. 在 [屬性] 視窗中，按一下**資料庫路線匯出工具**中**模型匯出工具**下拉式清單。  
  
2. 在 [屬性] 視窗中，設定**路線資料庫**屬性以指向路線資料庫的連接字串。  
  
3. 在 [屬性] 視窗中，設定**路線狀態**屬性設**已發佈**或是**部署**。  
  
   > [!NOTE]
   >  路線匯出至資料庫時**路線狀態**設為**已發佈**、 路線的會變成適用於[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]執行之前的時間之後的屬性設定為,**部署**。  
  
## <a name="security-operations"></a>安全性作業  
 使用路線設計工具，您可以保護機密資料，例如密碼和其他認證儲存在[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線，方法是加密此使用 X.509 憑證的資訊。  
  
#### <a name="select-the-x509-certificate-for-an-itinerary"></a>選取 路線的 X.509 憑證  
  
1.  在路線設計工具屬性視窗中，依序展開**加密憑證**屬性，，然後按一下**存放區位置**下拉式清單，並選取**CurrentUser**或是**LocalMachine**。 這將與目前的使用者或本機電腦關聯的 X.509 憑證存放區。  
  
2.  在 [屬性] 視窗中，按一下**存放區名稱**下拉式清單，然後選取其對應至您的憑證存放區的值。  
  
3.  在 [屬性] 視窗中，按一下 [加密憑證屬性旁的省略符號按鈕 （...），然後選取**X.509 憑證**中**選取憑證**] 對話方塊。  
  
#### <a name="remove-the-x509-certificate-from-an-itinerary"></a>移除路線的 X.509 憑證  
  
- 在路線設計工具屬性視窗中，依序展開**加密憑證**屬性，然後再把**存放區位置**屬性設為不同的值。 此解除關聯的舊憑證[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線的模型。  
  
#### <a name="disable-the-x509-certificate-validation"></a>停用的 X.509 憑證驗證  
  
在登錄編輯器中，移至子機碼**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk ESB Toolkit\2.0\Designer**，然後將**RequireX509Certificate**屬性值，以**false**。  
  
> [!NOTE]
>  如果您已安裝[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]子機碼是具有 64 位元支援作業系統上**HKEY_LOCAL_MACHINE\SOFTWARE\SysWOW64\Microsoft\BizTalk ESB Toolkit\2.0\Designer**。