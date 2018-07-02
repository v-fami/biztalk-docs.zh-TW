---
title: 設定 Oracle 資料庫繫結屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- binding properties, specifying at run time
- binding properties, specifying at design time
ms.assetid: c59a1b5c-b52b-4161-82de-c4d89bfce5c7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96922feab7c343893bfaa04ccbccd7c7e2f6a743
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981079"
---
# <a name="configure-the-binding-properties-for-oracle-database"></a>設定 Oracle 資料庫繫結屬性
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現可讓您控制其行為特性的數個繫結屬性。 本節提供設定的繫結屬性，從 Visual Studio 和 BizTalk Server 管理主控台的相關資訊。 從 Visual Studio 中，您必須產生針對特定作業的結構描述時指定繫結屬性。 從 BizTalk Server 中，必須指定的繫結屬性一部分傳送或接收埠的傳送或接收訊息，從 Oracle 資料庫。  

 如需繫結屬性的資訊，包括一份的繫結屬性[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  

## <a name="specifying-binding-properties-from-visual-studio"></a>指定繫結屬性，從 Visual Studio  
 從 Visual Studio 中，您必須指定使用的認證[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

#### <a name="to-specify-binding-properties-using-consume-adapter-service-add-in"></a>若要指定使用配接器服務增益集所使用的繫結屬性  

1.  以滑鼠右鍵按一下 BizTalk 專案，然後選取**加入產生的項目**。  

2.  在 **加入產生的項目**對話方塊方塊中，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |**類別**|按一下 **取用配接器服務**。|  
    |**範本**|按一下 **取用配接器服務**。|  

3.  若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。  

4.  在 **取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**oracleDBBinding**，，按一下 **設定**.  

5.  在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後指定不同的繫結屬性。  

6.  按一下 [確定] 。  

#### <a name="to-specify-binding-properties-using-add-adapter-metadata-wizard"></a>若要指定繫結屬性使用 新增配接器中繼資料精靈  

1. 以滑鼠右鍵按一下 BizTalk 專案，然後選取**加入產生的項目**。  

2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


   |    使用    |           以進行此動作            |
   |----------------|---------------------------------|
   | **類別** |     按一下 **新增介面卡**。      |
   | **範本**  | 按一下 **新增配接器中繼資料**。 |


3. 按一下 **[加入]**。 [新增配接器中繼資料精靈] 隨即開啟。  

4. 在 [新增配接器中繼資料精靈] 中，選取**Wcf-oracledb**。 選取的電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝和 BizTalk 資料庫的名稱。  

   > [!IMPORTANT]
   >  如果您已經設定 biztalk Wcf-oracledb 連接埠，請選取 從連接埠**連接埠**清單。  

5. 按 [下一步] 。  

6. 在 **取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**oracleDBBinding**，，按一下 **設定**.  

7. 在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。  

   > [!NOTE]
   >  如果您選取現有的 Wcf-oracledb 傳送埠時，您不需要指定繫結屬性。 從傳送埠組態，會挑選繫結屬性。 不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。 在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。  

8. 按一下 [確定] 。  

## <a name="specifying-binding-properties-from-the-biztalk-server-administration-console"></a>指定繫結屬性從 BizTalk Server 管理主控台  
 從 BizTalk Server 管理主控台中，您必須指定的繫結屬性，Wcf-custom 或 Wcf-oracledb 的連接埠組態的一部分。  

#### <a name="to-specify-binding-properties-for-the-wcf-custom-port"></a>若要指定 WCF 自訂連接埠的繫結屬性  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

3. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

4. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。  

5. 從**繫結的型別**下拉式清單中，選取**oracleDBBinding**。  

6. 在 **組態**方塊中指定不同的繫結屬性的值，然後按一下**確定**。  

#### <a name="to-specify-binding-properties-for-the-wcf-oracledb-port"></a>若要指定 Wcf-oracledb 連接埠的繫結屬性  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 新增 Wcf-oracledb 配接器至 BizTalk Server 管理主控台。 如需相關指示，請參閱 <<c0> [ 將 Oracle 資料庫配接器新增至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-database/adding-the-oracle-database-adapter-to-biztalk-server-administration-console.md)。  

3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

4. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增 Wcf-oracledb 配接器，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

5. 在 [傳輸屬性] 對話方塊中，按一下**繫結**索引標籤，然後指定繫結屬性的值。  

   > [!NOTE]
   >  繫結屬性會顯示根據您要設定傳送埠或接收埠。 比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。  

## <a name="see-also"></a>另請參閱  
[若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)