---
title: 設定 Oracle E-business Suite 繫結屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfdca8c8-4434-4a9f-8e2a-970988c2f685
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1e2d60ede3e41c08b15d3839f6ece41a68aa373
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989175"
---
# <a name="configure-the-binding-properties-for-oracle-e-business-suite"></a>設定 Oracle E-business Suite 繫結屬性
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]呈現可讓您控制其行為特性的數個繫結屬性。 本節提供設定的繫結屬性的相關資訊[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]進出[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須在產生特定作業的結構描述時指定的繫結屬性。 從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您必須指定的繫結屬性一部分傳送或接收埠來傳送或接收 Oracle E-business Suite 中的訊息。  

 如需繫結屬性的資訊，包括一份的繫結屬性[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  

## <a name="specifying-binding-properties-from-visual-studio"></a>指定繫結屬性，從 Visual Studio  
 從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您必須指定使用的繫結屬性[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。  

#### <a name="to-specify-binding-properties-using-consume-adapter-service-add-in"></a>若要指定使用配接器服務增益集所使用的繫結屬性  

1.  以滑鼠右鍵按一下您的 BizTalk 專案，然後按**加入產生的項目**。  

2.  在 **加入產生的項目**對話方塊方塊中，執行下列動作：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |**類別**|按一下 **取用配接器服務**。|  
    |**範本**|按一下 **取用配接器服務**。|  

3.  若要啟動**取用配接器服務** 對話方塊中，按一下**新增**。  

4.  在 **取用配接器服務** 對話方塊中，從**選取的繫結**下拉式清單中，選取**oracleEBSBinding**，然後按一下 **設定**.  

5.  在 [**設定介面卡**] 對話方塊中，按一下**繫結屬性**索引標籤，然後再指定不同的繫結屬性。  

6.  按一下 [確定] 。  

#### <a name="to-specify-binding-properties-using-add-adapter-metadata-wizard"></a>若要指定繫結屬性使用 新增配接器中繼資料精靈  

1. 以滑鼠右鍵按一下 BizTalk 專案，指向**新增**，然後按一下**新增產生的項目**。  

2. 在 **加入產生的項目**對話方塊方塊中，執行下列動作：  


   |    使用    |           以進行此動作            |
   |----------------|---------------------------------|
   | **類別** |     按一下 **新增介面卡**。      |
   | **範本**  | 按一下 **新增配接器中繼資料**。 |


3. 按一下 **[加入]**。 [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]隨即開啟。  

4. 在  [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，選取**Wcf-oracleebs**。 選取的電腦安裝 BizTalk Server 和 BizTalk 資料庫的名稱。  

   > [!IMPORTANT]
   >  如果您已經在 BizTalk 設定 Wcf-oracleebs 連接埠，請從連接埠清單中選取連接埠。  

5. 按 [下一步] 。  

6. 在 **取用配接器服務** 對話方塊中，從**選取的繫結**清單中，選取**oracleEBSBinding**，然後按一下 **設定**.  

7. 按一下 **繫結屬性**索引標籤，然後指定繫結的值，如果有的話，才會產生結構描述所需。 如需有關繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  

   > [!NOTE]
   >  如果您選取的現有 Wcf-oracleebs 傳送埠時，您需要指定繫結屬性。 從傳送埠組態，會挑選繫結屬性。 不過，您可以選擇指定繫結所需屬性在設計階段，如果有的話。 在此情況下，繫結屬性的新值將用於在設計階段時產生的中繼資料。 不過，在執行階段針對屬性繫結的傳送埠組態中指定的值將會適用。  

8. 按一下 [確定] 。  

## <a name="specifying-binding-properties-from-the-biztalk-server-administration-console"></a>指定繫結屬性從 BizTalk Server 管理主控台  
 從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須指定的繫結屬性，Wcf-custom 或 Wcf-oracleebs 的連接埠組態的一部分。  

#### <a name="to-specify-binding-properties-for-the-wcf-custom-port"></a>若要指定 WCF 自訂連接埠的繫結屬性  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

3. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取**Wcf-custom**，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

4. 在  **Wcf-custom 傳輸屬性** 對話方塊中，按一下**繫結** 索引標籤。  

5. 從**繫結的型別**清單中，選取**oracleEBSBinding**。  

6. 在 **組態**方塊，指定不同的繫結屬性的值，然後按一下**確定**。  

#### <a name="to-specify-binding-properties-for-the-wcf-oracleebs-port"></a>若要指定 Wcf-oracleebs 連接埠的繫結屬性  

1. 啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  

2. 新增 Wcf-oracleebs 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。 如需相關指示，請參閱 < [Oracle E-business Suite 配接器加入 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md)。  

3. 在主控台樹狀目錄中，依序展開**BizTalk 群組**，然後展開**應用程式**，然後展開 應用程式在其下您想要建立連接埠，然後按一下 **傳送埠**或**接收埠**。 在右窗格中，您可以選擇建立的連接埠，或選取現有的連接埠。  

4. 在 [連接埠屬性] 對話方塊中，從**型別**下拉式清單中，選取您稍早新增 Wcf-oracleebs 配接器，然後按一下**設定**。  

   > [!NOTE]
   >  若要查看 [接收埠的位置屬性] 對話方塊，請按一下**接收位置**索引標籤上的 [連接埠屬性] 對話方塊中，左窗格，然後按一下**新增**。  

5. 在 [傳輸屬性] 對話方塊中，按一下**繫結**索引標籤，然後指定繫結屬性的值。  

   > [!NOTE]
   >  繫結屬性會顯示根據您要設定傳送埠或接收埠。 比方說，與通知相關的繫結屬性沒有設定傳送埠，因為通知是輸入的作業，並且需要接收埠組態時。  

## <a name="see-also"></a>另請參閱  
 [若要建立 Oracle E-business Suite 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)