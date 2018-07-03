---
title: 檢視適用於 SAP 的報告 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0932ffc5-cde0-4d14-822f-713b760c3f12
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8643ef37e3fe4aec77cd9d218a171d37c2c24852
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974607"
---
# <a name="view-the-reports-for-sap"></a>適用於 SAP 的檢視報表
您已建立報表之後，您可以檢視使用 Visual Studio，或透過網路將它裝載在 Internet Information Services (IIS) 與存取報表伺服器上。 本主題提供有關如何檢視報表，在 Visual Studio，並使用 IIS 的指示。  
  
## <a name="prerequisites"></a>必要條件  
 然後再執行本主題所提供的程序，您必須產生報表中所述[使用 Data Provider for SAP 建立報表伺服器專案](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md)。  
  
### <a name="to-view-the-reports-in-visual-studio"></a>在 Visual Studio 中檢視報表  
  
1. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，以滑鼠右鍵按一下 [方案總管] 中的專案名稱，然後按一下**屬性**。  
  
2. 在 [報表屬性頁] 對話方塊中，按一下**Configuration Manager**，並清除底下的核取方塊**部署**資料行。 按一下 [ **關閉**]。  
  
3. 在 [報表屬性頁] 對話方塊中，如**StartItem**屬性中，選取報表的名稱，然後按一下**確定**。  
  
    ![指定報表伺服器專案的屬性](../../adapters-and-accelerators/adapter-sap/media/b3c500f7-840d-461f-945c-66db239d81b9.gif "b3c500f7-840d-461f-945c-66db239d81b9")  
  
4. 以滑鼠右鍵按一下 [方案總管] 中的專案名稱，然後按一下**建置**。  
  
5. 按下`F5`執行此專案以產生報表。  
  
   > [!IMPORTANT]
   >  在[!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)]，您可以按一下來查看報表**預覽** 索引標籤。在此情況下，後續的對話方塊會開啟 [預覽] 索引標籤中。  
  
6. 具有相同名稱與您針對報表指定的對話方塊會開啟。 建立資料來源時，如果您選擇**提示認證**選項，為 SAP 系統中，輸入使用者名稱和密碼，然後按一下**檢視報表**。  
  
    ![指定要產生報告的 SAP 認證](../../adapters-and-accelerators/adapter-sap/media/fa831aae-b2d1-4ba2-a23f-f7beeb8f898e.gif "fa831aae-b2d1-4ba2-a23f-f7beeb8f898e")  
  
7. 如果您指定查詢時建立報表伺服器專案需要參數，您必須輸入參數的值。 例如，查詢中指定[使用 Data Provider for SAP 建立報表伺服器專案](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md)主題，會要求您指定的參數，參數的值。  
  
    如有需要，指定參數的值，然後按一下 **檢視報表**。  
  
    ![指定要產生報表的參數](../../adapters-and-accelerators/adapter-sap/media/5deec152-771b-46b4-84da-dd176193d7f3.gif "5deec152-771b-46b4-84da-dd176193d7f3")  
  
### <a name="to-host-the-reports-on-report-server"></a>若要裝載報表伺服器上的報表  
  
1. 在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，以滑鼠右鍵按一下 [方案總管] 中的專案名稱，然後按一下**屬性**。  
  
2. 在 [報表屬性頁] 對話方塊中，按一下**Configuration Manager**，然後選取底下的核取方塊**部署**資料行。 按一下 [ **關閉**]。  
  
3. 在 [報表屬性頁] 對話方塊中，如**StartItem**屬性中，選取報表的名稱。  
  
4. 在 [報表屬性頁] 對話方塊中，如**TargetServerURL**屬性，指定報表伺服器的 URL，然後按一下**確定**。 例如：  
  
   ```  
   http://localhost/reportserver  
   ```  
  
    ![指定的報表伺服器 URL](../../adapters-and-accelerators/adapter-sap/media/397ddfd6-f3d2-4327-9bc3-1efa22dc2249.gif "397ddfd6-f3d2-4327-9bc3-1efa22dc2249")  
  
5. 以滑鼠右鍵按一下 [方案總管] 中的專案名稱，然後按一下**建置**。  
  
6. 以滑鼠右鍵按一下 [方案總管] 中的專案名稱，然後按一下**部署**。  
  
7. 啟動 IIS。 按一下 **開始**，按一下**執行**，型別`inetmgr`，然後按`Enter`。  
  
8. 在  **Internet Information Services (IIS) 管理員**嵌入式管理單元中，展開電腦名稱，展開**網站**，展開**Default Web Site**，以滑鼠右鍵按一下**ReportServer**，然後按一下**瀏覽**。  
  
9. 在右窗格中，按一下專案名稱，然後按一下報表名稱。  
  
10. 建立資料來源時，如果您選擇**提示認證**選項，輸入 SAP 系統的使用者名稱和密碼，然後按一下**檢視報表**。  
  
11. 如果您指定查詢時建立報表伺服器專案需要參數，您必須輸入參數的值。 例如，查詢中指定[使用 Data Provider for SAP 建立報表伺服器專案](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-to-create-a-report-server-project.md)主題，會要求您指定的參數，參數的值。  
  
     如有需要，指定參數的值，然後按一下 **檢視報表**。  
  
     ![指定要產生報表的參數](../../adapters-and-accelerators/adapter-sap/media/221c8c12-4e4f-47f5-9289-9e9212cf6e25.gif "221c8c12-4e4f-47f5-9289-9e9212cf6e25")  
  
    > [!TIP]
    >  您也可以直接從網頁瀏覽器檢視，讓報表的 URL。 報表的一般 URL `is http://localhohost/reportserver/<report_name>`。  
  
## <a name="see-also"></a>另請參閱  
 [搭配使用 Data Provider for SAP 與 SSRS](../../adapters-and-accelerators/adapter-sap/use-the-data-provider-for-sap-with-ssis.md)