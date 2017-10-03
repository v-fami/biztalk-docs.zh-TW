---
title: "連接到 Oracle E-business Suite，在 Visual Studio 中使用 新增配接器服務參考外掛程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fe4d1b7-8201-4816-ae90-020520f29714
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49eaa30c63d373ba20ae19f470405b851475d93a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-oracle-e-business-suite-in-visual-studio-using-add-adapter-service-reference-plug-in"></a>連接到 Oracle E-business Suite，在 Visual Studio 中使用 新增配接器服務參考外掛程式
若要連接到 Oracle E-business Suite 使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]在.NET 程式設計方案，您必須使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]。 本主題說明如何使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
## <a name="connecting-to-oracle-e-business-suite-using-the-add-adapter-service-reference-plug-in"></a>連接到 Oracle E-business Suite 使用新增配接器服務參考外掛程式  
 執行下列步驟來連接 Oracle E-business Suite 使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-connect-to-oracle-e-business-suite"></a>若要連接到 Oracle E-business Suite  
  
1.  若要使用連接[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]程式設計方案中：  
  
    1.  建立使用 Visual Studio 專案。  
  
    2.  以滑鼠右鍵按一下方案總管 中的專案，然後按一下**新增配接器服務參考**。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]隨即開啟。  
  
2.  從**選取繫結**下拉式清單中選取**oracleEBSBinding**按一下**設定**。  
  
3.  在**設定配接器**對話方塊中，按一下**安全性** 索引標籤，並從**用戶端認證類型**下拉式清單方塊中，選取**的使用者名稱**並指定使用者名稱和密碼，以連接到 Oracle E-business Suite 的資訊。  
  
    |||  
    |-|-|  
    |使用|動作|  
    |**若要使用 Oracle 資料庫的認證進行連接**|指定**ClientCredentialType**內容繫結至**資料庫**和指定的資料庫認證**使用者名**和**密碼**文字方塊。|  
    |**使用 Oracle E-business Suite 認證進行連接**|指定**ClientCredentialType**內容繫結至**EBusiness**指定 Oracle E-business Suite 認證**使用者名**和**密碼**文字方塊。 在此情況下，您也必須指定 Oracle 資料庫認證**OracleUserName**和**OraclePassword**繫結屬性。|  
    |**如果 ClientCredentialType 設定為 「 資料庫 」，請使用 Windows 驗證進行連接**|指定"/"表示**使用者名**文字方塊並保留**密碼**文字方塊留白。|  
    |**如果 ClientCredentialType 設定為"EBusiness 「 使用 Windows 驗證進行連接**|指定 Oracle E-business Suite 認證**使用者名**和**密碼**文字方塊。 您也必須指定"/"表示**OracleUserName**繫結屬性和保持**OraclePassword**繫結屬性為空白。|  
  
4.  按一下**URI 屬性**索引標籤，然後指定連線參數的值。 如需有關連線 URI 的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)。  
  
    > [!NOTE]
    >  如果連接參數可以包含任何保留的字元，您必須指定以-處於**URI 屬性**索引標籤上，也就是不使用任何逸出字元。 不過，如果您指定的 URI 中直接**設定 URI**欄位和連接參數可以包含保留的字元，您必須指定連接參數使用適當的逸出字元。  
  
5.  按一下**繫結屬性**索引標籤，然後再指定繫結屬性值，如果任何項目，做為目標的作業所需。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
6.  按一下 **[確定]**。  
  
7.  按一下 **[連接]**。 建立連接之後，連線狀態會顯示為**Connected**。  
  
     下圖顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]之後立即建立連線。 圖形化使用者介面是相同的[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
     ![使用配接器服務對話方塊](../../adapters-and-accelerators/adapter-oracle-ebs/media/6a2b21ed-0fd2-4874-a6a6-e59a467533f8.gif "6a2b21ed-0fd2-4874-a6a6-e59a467533f8")  
  
     [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]顯示不同的節點包含各種可以 Oracle E-business Suite 和 Oracle 資料庫執行的作業。 如需有關如何在不同的節點下的中繼資料的分類方式的詳細資訊，請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中使用 新增配接器中繼資料精靈](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-metadata-wizard.md)。  
  
## <a name="see-also"></a>另請參閱  
 [連接到 Oracle E-business Suite，Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)   
 [連接到 Oracle E-business Suite 使用 Windows 驗證](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)