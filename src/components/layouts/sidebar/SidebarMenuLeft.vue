<template>
  <div>
    <div class="mobile-menu-left-overlay"></div>
    <nav class="side-menu">
      <ul class="side-menu-list">
        <li class="grey with-sub">
          <a href="/">
            <span class="font-icon font-icon-dashboard"></span>
            <span class="lbl">Painel de Controle</span>
          </a>
        </li>

        <li v-if="isRoleAdmin || isRoleEditor || isRoleAuditor" class="brown with-sub">
          <span>
            <i class="fa fa-tags"></i>
            <span class="lbl">Catálago</span>
          </span>
          <ul>
            <li>
              <a href="#">
                <span class="lbl">Categorias</span>
              </a>
            </li>
            <li>
              <a href="#">
                <span class="lbl">Produtos</span>
              </a>
            </li>
            <!-- <li><a href="#"><span class="lbl">Tipos de assinatura</span></a></li>
            <li><a href="#"><span class="lbl">Filtros</span></a></li>-->
            <li>
              <router-link :to="{ name: 'catalogs.attributes.list'}">
                <span class="lbl">Atributos</span>
              </router-link>
            </li>
            <!-- <li><a href="#"><span class="lbl">Opções</span></a></li> -->
            <li>
              <router-link :to="{ name: 'catalogs.brands.list'}">
                <span class="lbl">Marcas</span>
              </router-link>
            </li>
            <!-- <li><a href="#"><span class="lbl">Downloads</span></a></li> -->
            <li>
              <a href="#">
                <span class="lbl">Comentários</span>
              </a>
            </li>
            <li>
              <router-link :to="{ name: 'catalogs.pages.list'}">
                <span class="lbl">Páginas de informações</span>
              </router-link>
            </li>
          </ul>
        </li>

        <li class="blue with-sub">
          <span>
            <i class="fa fa-users"></i>
            <span class="lbl">Clientes</span>
          </span>
          <ul>
            <li>
              <a href="#">
                <span class="lbl">Clientes</span>
              </a>
            </li>
            <li>
              <a href="#">
                <span class="lbl">Tipos de clientes</span>
              </a>
            </li>
            <li>
              <a href="#">
                <span class="lbl">Aprovar clientes</span>
              </a>
            </li>
            <li>
              <a href="#">
                <span class="lbl">Personalizar cadastro</span>
              </a>
            </li>
          </ul>
        </li>


        <li v-if="isRoleAdmin || isRoleAuditor" class="purple with-sub">
          <span>
            <i class="fa fa-cog"></i>
            <span class="lbl">Configurações</span>
          </span>
          <ul>

            <li class="purple with-sub">
              <span>
                <span class="lbl">Gerenciar usuários</span>
              </span>
              <ul>
                <li v-if="isRoleAdmin">
                  <router-link :to="{ name: 'settings.users.list'}">
                    <span class="lbl">Gerenciar usuários</span>
                  </router-link>
                </li>
              </ul>
            </li>

            <li v-if="isRoleAdmin" class="purple with-sub">
              <span>
                <span class="lbl">Gerenciar Permissões</span>
              </span>
              <ul>
                <li>
                  <router-link :to="{ name: 'settings.roles.list'}">
                    <span class="lbl">Funções</span>
                  </router-link>
                </li>
              </ul>
              <ul>
                <li>
                  <router-link :to="{ name: 'settings.privileges.list'}">
                    <span class="lbl">Privilégios</span>
                  </router-link>
                </li>
              </ul>
            </li>

            <li v-if="isRoleAdmin" class="purple with-sub">
              <span>
                <span class="lbl">Manutenção</span>
              </span>
              <ul>
                <li>
                  <a href="#">
                    <span class="lbl">Backup / Restaurar</span>
                  </a>
                </li>
                <li>
                  <a href="#">
                    <span class="lbl">Log de erros</span>
                  </a>
                </li>
              </ul>
            </li>
          </ul>
        </li>

        <li class="blue-dirty with-sub">
          <span>
            <i class="fa fa-bar-chart-o"></i>
            <span class="lbl">Relatórios</span>
          </span>
          <ul>
            <li>
              <a href="#">
                <span class="lbl">Relatórios</span>
              </a>
            </li>

          </ul>
        </li>
      </ul>
    </nav>
    <!--.side-menu-->
  </div>
</template>
<script>
import { isAclToLink } from "@/utils/authorizations-helpers";

export default {
  name: "SidebarMenuLeft",
  data() {
    return {
      isRoleAdmin: false,
      isRoleEditor: false,
      isRoleAuditor: false,
      isRoleFinance: false,
    };
  },
  created() {
    this.isRoleAdmin = isAclToLink("ADMIN");
    this.isRoleEditor = isAclToLink("STAFF_EDITOR");
    this.isRoleAuditor = isAclToLink("STAFF_AUDITOR");
    this.isRoleFinance = isAclToLink("STAFF_FINANCE");
  }
};
</script>
